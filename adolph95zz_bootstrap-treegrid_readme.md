
 # 功能：依赖bootstrap-table实现treegrid，
 * 来源：参照[JS组件系列——自己动手扩展BootstrapTable的treegrid功能](http://www.cnblogs.com/landeanfen/p/6924895.html) 例子做了部分改动
 * 作者：lds2013@163.com
 * 日期：2017年10月5日
 * 修改：2018年4月20日
 # 内容：
 *       1、支持自定义收缩、展开图标；
 *       2、支持自定义父级ID传入，默认ParentId；
 *       3、父级ID最顶层改为0；
 *       4、修改最后子级前的小图标；
 *       5、支持展开、收缩事件；

 # 用法： 
```
  
  
  

$('#tb').bootstrapTable({
        method: 'post',
        url: '/HR/HrDept/GetList',
        singleSelect: true,//单行选择
        clickToSelect: true,//点击行时自动选择
        striped: true,//是否显示行间隔色
        treeView: true,//是否显示树形视图
        treeId: "DeptID",//定义关键字段来标识树节点
        treeField: "DeptName",//定义树节点字段
        treeParentId: "MasterID", //定义父级ID字段
        treeRootLevel: 1,//树根的级别
        treeCollapseAll: false,//是否全部折叠，默认折叠 
        uniqueId: "DeptID", //每一行的唯一标识，一般为主键列
        columns:
        [
          { field: 'ck', checkbox: true },
          { field: 'DeptID', title: '机构ID'},
          { field: 'MasterID', title: '上级ID', visible: false },
          { field: 'DeptName', title: '机构名称' }
        ]
       });
```

 * 注意事项：暂无
          

# 效果图
![效果图](https://gitee.com/uploads/images/2018/0421/135130_6a98b4df_342448.jpeg "grid.jpg")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)