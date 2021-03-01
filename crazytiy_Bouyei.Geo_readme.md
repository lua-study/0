# bouyei.Geo

#### 介绍
是Geometry GIS常用格式解析处理库，为方便灵活高效无依赖处理常用的数据文件格式提供支持，对ogc(geojson,wkt,wkb等),shpfile,esri mdb等的数据格式进行解析和生成。增加支持常用的geometry算法支持，如:高斯正反算，平面面积计算，椭球面积计算等。

Bouyei.Geo 基于.net framework 4.5.1+

Bouyei.GeoCore 基于.net core 2.0+

Bystd.Geo 基于.net standard 2.0+

#### 软件架构
软件架构说明

1、支持常用geometry数据格式解析转换。

2、支持基本geometry算法如相交和面积计算等。

3、精简尽量无依赖第三方库方便可修改可移植。

4、最大限度的简单引用和入手学习使用。

#### 安装教程

1. vs or vs code

#### 使用说明

1.  nuget install
2.  面积计算

            string wktstr = "POLYGON ((36379440.1493 2936717.206599999, 36379425.4384 2936710.4860999994, 36379423.0042             2936716.307, 36379437.133 2936723.318499999, 36379440.1493 2936717.206599999))";

            GeometryPlane plane = new GeometryPlane();
            var area = plane.Area(wktstr);

            GeometryEllipse geo = new GeometryEllipse();
            var ellipse = geo.Area(wktstr);

            var dist = geo.Distance(new Coordinate()
            {
                X = 36379440.1493,
                Y = 2936717.206599999
            },
             new Coordinate()
             {
                 X = 36379425.4384,
                 Y = 2936710.4860999994
             });

            var geopoint = new Coordinate()
            {
                X = 36367729.9624,
                Y = 2941185.8308
            };

            var bl = plane.XYtoLB(geopoint);
            var bxy = plane.LBtoXY(bl);
3.  esri mdb解析

            string connstr = @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=E:\LINE.mdb;";
            using (IAdoProvider provider = AdoProvider.CreateProvider(connstr, FactoryType.OleDb))
            {
                var rt = provider.Query (new Parameter("select top 1 SHAPE as wkb from multipoint"));
                var items = rt.Result;
                List  geos = new List ();
                foreach (var item in items)
                {
                    EsriMdbParser wkbParser = new  EsriMdbParser(item.wkb);
                    var geo = wkbParser.FromReader();

                    //生成wkt
                   // string wkt= geo.ToWkt();

                    geos.Add(geo);
                }
            }
4.geojson 解析


            string file = "C:\\3DCity.json";// AppContext.BaseDirectory + "testfiles\\feature.geojson";//"C:\\3DCity.json";
            string content = File.ReadAllText(file, Encoding.UTF8);
            GeoJsonParser json = new GeoJsonParser(content);

            var geo = json.ToFeatures ();

            List  coords = new List ();
            coords.Add(new double[] { 1, 2 });
            coords.Add(new double[] { 2, 3 });

            var collection = new FeatureCollection ()
            {
                name = "八渡镇",
                features = new Feature [] {
                 new Feature (){
                 properties=new attr(){  name="乃言村",code="522327"},
                 geometry=new JsonLineString(){
                 coordinates=coords
              }
             }
            }
            };
            var str = json.ToWrite (collection);

#### 参与贡献

1.  Fork 本仓库
2.  新建 Bouyei.Geo_xxx 分支
3.  提交代码
4.  新建 Pull Request


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)