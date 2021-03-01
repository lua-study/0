 
 
 
 
 

**cesium-sensors**: A Cesium plugin for visualizing sensor volumes.

**Cesium version**: Tested against [1.6](http://cesiumjs.org/downloads.html). Post a message to the [Cesium forum](http://cesiumjs.org/forum.html) if you have compatibility issues.

**License**: Apache 2.0.  Free for commercial and non-commercial use.  See [LICENSE.md](LICENSE.md).

**Usage**

Prebuilt minified and unminified versions of the plugin are in the [Build](Build/) directory.  Include the `CesiumSensors.js` file using a `script` tag after the `Cesium.js` `script` tag.

The plugin automatically adds support for the CZML properties `agi_conicSensor`, `agi_customPatternSensor`, and `agi_rectangularSensor`.  The corresponding `Entity` properties are `conicSensor`, `customPatternSensor`, and `rectangularSensor`.

In order to load data directly into `Entity` objects that you create directly, you must call `entity.addProperty` to create each of the sensor properties you wish to use.  The CZML processing does this automatically.

```html
  
  
 
// To create an entity directly
var entityCollection = new Cesium.EntityCollection();

var entity = entityCollection.getOrCreateEntity('test');
entity.addProperty('conicSensor');

// configure other entity properties, e.g. position and orientation...

entity.conicSensor = new CesiumSensors.ConicSensorGraphics();
entity.conicSensor.intersectionColor = new Cesium.ConstantProperty(new Cesium.Color(0.1, 0.2, 0.3, 0.4));
 
```

**Example**

Simple examples are included in the [Examples](Examples/) folder.  To run locally, run `npm install`, then run `node server.js` and navigate to [http://localhost:8080](http://localhost:8080) and select the example application to run.

**Build**

To build, run `npm install`, then run `node build.js`.

**Contributions**

Contributions welcome.  We use the [same CLA as Cesium](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CONTRIBUTING.md).  Please email yours before opening a pull request.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)