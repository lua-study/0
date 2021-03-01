# com.checcdata.cordova.plugin

使用高德地图sdk进行导航

## 安装
`ionic cordova plugin add https://gitee.com/checcdata/amapplugin.git --save `

## 配置
更多详情请看https://gitee.com/checcdata/amapplugin.git#readme
### Android

*  修改 plugin.xml(:23) 文件中的高德地图android key

` `

### ionic2+调用方法

```Position接口
export interface Position {
    lng: number,
    lat: number,
    offsetLng?: number,
    offsetLat?: number
    poi?: string
}
```

```导航Service
import {Injectable} from '@angular/core';
declare var AMapPlugin;

@Injectable()
export class NativeService {
  constructor() { }
  
    /**
     * @param {Position} startPoint 开始坐标
     * @param {Array } wayPoints 途经坐标
     * @param {Position} endPoint 结束坐标
     * @param {number} aMapNaviType 导航类型：
     * 0：开车
     * 1：步行
     * 2：骑行
     * @param {number} aMapPageType 导航页面类型
     * 0：路径
     * 1：导航
     * @param {AMapCarInfo} aMapCarInfo 车辆信息
     * @returns {Observable }
     */
    navigation (startPoint: Position, wayPoints:Array  ,endPoint: Position,aMapNaviType:number,aMapPageType:number, aMapCarInfo: AMapCarInfo): Observable  {
        return Observable.create(observer => {
            if (this.platform.is('mobile') && !this.platform.is('mobileweb')) {

                let length = wayPoints.length;

                AMapPlugin.navigation({
                    lng: startPoint.lng,
                    lat: startPoint.lat,
                    poi: startPoint.poi
                }, {
                    lng: startPoint.lng,
                    lat: startPoint.lat,
                    poi: startPoint.poi
                }, {
                    lng: endPoint.lng,
                    lat: endPoint.lat,
                    poi: endPoint.poi
                }, {
                    aMapNaviType:aMapNaviType
                },  {
                    aMapPageType:aMapPageType
                },{
                    carNumber: aMapCarInfo.carNumber,
                    isRestriction: aMapCarInfo.isRestriction,
                    carType: aMapCarInfo.carType,
                    vehicleHeight: aMapCarInfo.vehicleHeight,
                    vehicleWeight: aMapCarInfo.vehicleWeight,
                    vehicleLoad: aMapCarInfo.vehicleLoad,
                    vehicleLoadSwitch: aMapCarInfo.vehicleLoadSwitch,
                    vehicleWidth: aMapCarInfo.vehicleWidth,
                    vehicleLength: aMapCarInfo.vehicleLength,
                    vehicleSize: aMapCarInfo.vehicleSize,
                    vehicleAxis: aMapCarInfo.vehicleAxis
                }, message => {
                    observer.next(message);
                }, err => {
                    this.logger.log(err, '导航失败');
                    this.alert('提示信息', '导航失败');
                    observer.error(false);
                });
            } else {
                this.alert('提示信息', '非手机环境不能导航');
                observer.error(false);
            }
        });
    }
}

```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)