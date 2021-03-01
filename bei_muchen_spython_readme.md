# Python解释器spython介绍#
## 简介 ##
　　出于个人爱好和某种需求，我再16年对python的解释器产生了浓厚兴趣，并且下定决心重新实现一个版本。我个人再游戏服务器开发中，对c++嵌入lua和python都有着丰富应用经验，自认为对二者的优劣有着深刻的理解。python针对lua的最大优势是python是完备的程序语言，类、模块包括丰富的库和方便好用的字符串操作，可以说python用来实现功能会优雅很多，而lua最大的优势就是小巧高效，另外lua的lua_state是可以有多个实例的，这样就可以多线程使用lua（一个线程单独一个lua_state）,而python解释器因为有全局解释器锁，所以无法实现多python解释器实例。考虑到在嵌入python的应用场景中，所用到python的功能都是比较简单通用的功能，比如类、模块，函数，一些复杂的类库也不常用，所以我就想实现一个不使用全局解释器锁，可以有多个python解释器锁的解释器。所以16年底，我自己实现了一下python解释器第一版，第一版是使用AST虚拟语法树直接解析的，虽然做了必要的优化，但是性能。。。。仍然不忍直视。平常我一直吐槽python跑的没有lua快，但是吐槽是一码事，自己实现真的就是另一码事了。我仔细分析了第一版性能低的原因是选错了路！python的虚拟机是讲语法树翻译成ByteCode，然后有个Virtual Machine不断的解释bytecode，而vm的运行又分堆栈模式和寄存器模式，python就是堆栈模式的，而lua是寄存器模式的，寄存器模式是现在的趋势，这也是lua跑到更快的重要原因。我的第一版VM用AST直接跑，选错了路，无论如何也太快不了。但是我仍然把这个第一版打了个分支，分享出来，因为当我实现用寄存器模式的VM的时候，感觉无论如何也无法设计的像AST直接解析的VM那样优雅、直接。AST直接解析的方式真的太直观了，虽然效率很低，但是其仍然有很大的应用价值。比如protocolbuff、thrift这些通过定义语法文件生成代码的这类工具，对语法解析的效率要求不高，那么这个版本的VM再这些领域还是有很大的参考价值。
　　内部实现层次：

![Alt text](http://images.cnblogs.com/cnblogs_com/zhiranok/287956/o_show.jpg)
## Python BNF ##
　　一提到实现脚本解释器，估计很多人都会挠头，不知道从何入手。刚开始我也是这样，我把大学里的编译原理从床底下一堆打入冷宫的数量翻出来，一顿猛看。但是仍然没有找到很大头绪，后来我就在python.org上一顿逛，也下载了python的源码分析，源码目录有python的BNF描述文件，因为我已经看过一遍编译原理了，BNF就看的很懂，从头到尾读了一遍了以后，灵光乍现啊！BNF就是完整的解析python语法的流程说明啊！截取一小段做个说明：
```python
compound_stmt: if_stmt | while_stmt | for_stmt | try_stmt | with_stmt | funcdef | classdef | decorated
if_stmt: 'if' test ':' suite ('elif' test ':' suite)* ['else' ':' suite]
while_stmt: 'while' test ':' suite ['else' ':' suite]
for_stmt: 'for' exprlist 'in' testlist ':' suite ['else' ':' suite]
try_stmt: ('try' ':' suite
         ((except_clause ':' suite)+
          ['else' ':' suite]
          ['finally' ':' suite] |
         'finally' ':' suite))
with_stmt: 'with' with_item (',' with_item)*  ':' suite
with_item: test ['as' expr]
# NB compile.c makes sure that the default except clause is last
except_clause: 'except' [test [('as' | ',') test]]
suite: simple_stmt | NEWLINE INDENT stmt+ DEDENT
```
　　简单解释下，python的Grammar BNF是从顶之下递归描述的。上面最上边定义的是compound_stmt复杂语句，而compound_stmt有if、while、for、try、with、函数定义、类定义、修饰器定义几种，下面紧接着定义了if语句if_stmt的语法规则，这样在c++实现解析python语法的时候，就可以从顶向下按照这个BNF尝试解析，如果不满足这个BNF语法要求的就报错。我为了生成跟这个BNF一致的代码结构，写了个python脚本解析这个BNF自动生成C++的解析函数。生成的C++代码示例如下：
```cpp
class Parser{
public:
  ExprASTPtr parse(Scanner& scanner);

  //! single_input: NEWLINE | simple_stmt | compound_stmt NEWLINE
  ExprASTPtr parse_single_input();
  //! file_input: (NEWLINE | stmt)* ENDMARKER
  ExprASTPtr parse_file_input();
  //! eval_input: testlist NEWLINE* ENDMARKER
  ExprASTPtr parse_eval_input();
  //! decorator: '@' dotted_name [ '(' [arglist] ')' ] NEWLINE
  ExprASTPtr parse_decorator();
  //! decorators: decorator+
  ExprASTPtr parse_decorators();
  //! decorated: decorators (classdef | funcdef)
  ExprASTPtr parse_decorated();
  //! funcdef: 'def' NAME parameters ':' suite
  ExprASTPtr parse_funcdef();
  //! parameters: '(' [varargslist] ')'
  ExprASTPtr parse_parameters();
  //! varargslist: ((fpdef ['=' test] ',')*
  //!               fpdef ['=' test] (',' fpdef ['=' test])* [','])
  ExprASTPtr parse_varargslist();
  //! fpdef: NAME | '(' fplist ')'
  ExprASTPtr parse_fpdef();
  //! fplist: fpdef (',' fpdef)* [',']
  ExprASTPtr parse_fplist();
  //! stmt: simple_stmt | compound_stmt
  ExprASTPtr parse_stmt();
  //! simple_stmt: small_stmt (';' small_stmt)* [';'] NEWLINE
  ExprASTPtr parse_simple_stmt();
  //! small_stmt: (expr_stmt | print_stmt  | del_stmt | pass_stmt | flow_stmt |
  //!              import_stmt | global_stmt | exec_stmt | assert_stmt)
  ExprASTPtr parse_small_stmt();
  //! expr_stmt: testlist (augassign (yield_expr|testlist) |
  ExprASTPtr parse_expr_stmt();
.................................
```
### Scanner的实现 ###
　　scanner负责解析python代码，把python代码分隔这一个个Token对象，并且Token对象的定义如下：

```cpp
struct Token{
  Token():nTokenType(0), nVal(0), fVal(0.0), nLine(0){
  }

  std::string dump() const;
  int             nTokenType;
  int64_t         nVal;
  double          fVal;
  std::string     strVal;
  int             nLine;
};

enum ETokenType {
    TOK_EOF = 0,
    //TOK_DEF = -2,
    TOK_VAR = -4,
    TOK_INT = -5,
    TOK_FLOAT = -6,
    TOK_STR = -7,
    TOK_CHAR = -8,
};

```
　　nTokenType定义为ETokenType的枚举。Scanner只扫描python代码，而不解析语法，所有的python代码都会解析成要么整数，要么浮点数要么字符串。这个跟原生的python是有区别的，原生python的数字对象可以表达任意数字，但是为了实现简便，做了简化处理，这也是参考了lua的实现方式每token对象会记录所属的行号，方便语法报错提供有用的信息。
　　具体scanner的实现就不贴出来了，感兴趣的可以去查看源码，还是比较简单的。
### Parser的实现 ###
　　Parser的头文件是脚本解析BNF自动生成的。负责把scanner解析的token列表，按照BNF的规则构造成AST。AST节点对象定义为ExprAST：

```cpp

class ExprAST {
public:
    ExprAST(){
    }
    virtual ~ExprAST() {}
    virtual PyObjPtr& eval(PyContext& context) = 0;

    unsigned int getFieldIndex(PyContext& context, PyObjPtr& obj);

    virtual PyObjPtr& getFieldVal(PyContext& context);
    virtual PyObjPtr& assignVal(PyContext& context, PyObjPtr& v){
        PyObjPtr& lval = this->eval(context);
        lval = v;
        return lval;
    }
    virtual void delVal(PyContext& context){
        PyObjPtr& lval = this->eval(context);
        lval = NULL;
    }

    virtual int getType() {
        return 0;
    }

public:
    std::string name;
    ExprLine    lineInfo;
    //std::vector  >  module2objcet2fieldIndex;
    std::vector                   module2objcet2fieldIndex;
};
class PyObj {
public:
    RefCounterData* getRefData(){
        return &refdata;
    }
    void release();
    typedef PySmartPtr  PyObjPtr;
    PyObj():m_pObjIdInfo(NULL), handler(NULL){}
    virtual ~PyObj() {}

    int getType() const;
    virtual int getFieldNum() const { return m_objStack.size(); }
    static std::string dump(PyContext& context, PyObjPtr& self, int preBlank = 0);

    virtual PyObjPtr& getVar(PyContext& c, PyObjPtr& self, ExprAST* e);
    virtual const ObjIdInfo& getObjIdInfo() = 0;

    void clear(){
        m_objStack.clear();
    }
    inline PyObjHandler* getHandler() { return handler; }
    inline const PyObjHandler* getHandler() const { return handler; }
public:
    std::vector     m_objStack;
    ObjIdInfo*               m_pObjIdInfo;
    PyObjHandler*            handler;
    RefCounterData           refdata;
};
typedef PyObj::PyObjPtr PyObjPtr;
```
　　ExprAST抽象了AST节点的几个操作。最主要的就是求值操作eval。比如100求值就是100，'abc'求值就是字符串'abc',生成对应的值对象。每个值对象都继承PyObj。每个PyObj都会定义ObjHander接口用于实现python对象的各个操作，比如+、-、/等，不同的python值对象，响应的操作是不一样，这里利用了c++的多态。

```cpp
class PyObjHandler{
public:
  virtual ~PyObjHandler(){}

  virtual int getType() const = 0;

  virtual std::string handleStr(PyContext& context, const PyObjPtr& self) const;
  virtual std::string handleRepr(PyContext& context, const PyObjPtr& self) const;
  virtual int handleCmp(PyContext& context, const PyObjPtr& self, const PyObjPtr& val) const;
  virtual bool handleBool(PyContext& context, const PyObjPtr& self) const;
  virtual bool handleEqual(PyContext& context, const PyObjPtr& self, const PyObjPtr& val) const;
  virtual bool handleLessEqual(PyContext& context, const PyObjPtr& self, const PyObjPtr& val) const;
  virtual bool handleGreatEqual(PyContext& context, const PyObjPtr& self, const PyObjPtr& val) const;
  virtual bool handleContains(PyContext& context, const PyObjPtr& self, const PyObjPtr& val) const;

  virtual bool handleLess(PyContext& context, const PyObjPtr& self, const PyObjPtr& val) const;
  virtual bool handleGreat(PyContext& context, const PyObjPtr& self, const PyObjPtr& val) const;

  virtual PyObjPtr& handleAdd(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleSub(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleMul(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleDiv(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleMod(PyContext& context, PyObjPtr& self, PyObjPtr& val);


  virtual PyObjPtr& handleIAdd(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleISub(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleIMul(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleIDiv(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual PyObjPtr& handleIMod(PyContext& context, PyObjPtr& self, PyObjPtr& val);

  virtual PyObjPtr& handleCall(PyContext& context, PyObjPtr& self, std::vector & allArgsVal,
                               std::vector & argAssignVal);
  virtual size_t    handleHash(PyContext& context, const PyObjPtr& self) const;
  virtual bool handleIsInstance(PyContext& context, PyObjPtr& self, PyObjPtr& val);
  virtual long handleLen(PyContext& context, PyObjPtr& self);
  virtual PyObjPtr& handleSlice(PyContext& context, PyObjPtr& self, PyObjPtr& startVal, int* stop, int step);
  virtual PyObjPtr& handleSliceAssign(PyContext& context, PyObjPtr& self, PyObjPtr& k, PyObjPtr& v);
  virtual void handleSliceDel(PyContext& context, PyObjPtr& self, PyObjPtr& k){}

  virtual void handleRelese(PyObj* data);
};
```

### Python库的实现 ###
　　实现的python库列表如下：
1.  list dict tuple copy string
2.  datetime
3.  json
4.  math
5.  os
6.  random
7.  open stringio
8.  struct
9.  sys
10. weak

### 总结 ###
　　spython就是small python，本来想实现最简版本的python解释器，后来实现的比较顺，一口气把常用的python库都实现了。spython最成功的部分就是ast的解析和执行，代码结构清晰完全按照bnf的流程来，很直接明了。缺点主要有二。一是语法报错还是太简陋，不够友好。二是性能达不到原生python的性能。前文已经说过了，要达到甚至超过原生python的水平，必须要实现基于寄存器的VM，这个已经着手再弄了，暂时还不会放出代码，等差不多成型了再放出来吧。
　　代码地址：https://git.oschina.net/ownit/spython
　　构建：Linux下直接make就可以了，win下需要用dev c++

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)