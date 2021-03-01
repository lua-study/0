# AsyncClient

#### 介绍
帧同步客户端

#### 软件架构
lotus   unity相关的通用方法
peony   与引擎无关,纯C#方法
```
//动作行为接口类定义
class BaseAction
{
    //只是提供接口
    void updateLogic()
}

class MoveTo : BaseAction
{
    
    StartPosition;
    EndPosition;
    Distance = EndPosition - StartPosition;
    MoveTime;//动作预计花费的时间
    MoveElpaseTime;//这次动作,从开始到现在花费的时间

    override void updateLogic()
    {

    }
}

class ActionManager
{
    List  actionList;//动作链表
    void updateLogic()
    {
        for action in actionList
        {
            action.updateLogic()
        }
    }
}

//物体
class UnityObject
{
    GameObject
    LastPosition//最后位置
    LogicPosition//逻辑位置

    void updateRenderPosition(float interpolation/**/)
    {
        //在最后坐标和逻辑坐标中间做差值
        Vector3.Lerp(LastPosition,LogicPosition,interpolation);

    }

}

class BaseObject:UnityObject
{
    MoveTo moveAction;
    ActionManager actionManager;

    StateMachine machine;

    void init()
    {
        actionmanager = new ActionManager();
    }

    void moveTo(startPos,endPos,time)
    {
        moveToAction = new MoveTo()
        actionManager.addAction(moveToAction);
    }
}

//状态机
class LiveObject:BaseObject
{
    //玩家各种属性
    LiveObject unity;
    //上一次状态
    string PrevState;
    //这一次状态
    string currStat;
    void updateLogic()
    {

    }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)