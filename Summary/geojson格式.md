# GeoJSON格式

## 概述
GeoJSON文件是指使用对象的形式，表达地理空间数据的JSON文件。文件内容中定义了多种类型的JSON对象结构，可表述不同类型的地理要素、属性以及空间范围。dataviz所使用的GeoJSON文件，采用的是RFC7946标准（2016年8月发布），由互联网工程任务组（IETF）与原始规范作者共同制定，（官网：http://www.rfc-editor.org/info/rfc7946）。  
可用于dataviz渲染的GeoJSON文件应按照标准的GeoJSON格式，可以根据需要并在GeoJSON规则约束下拓展，如下结构：
```
{
  "type": "FeatureCollection",
  "features": [
        {
            "type":"Feature",
            "properties":{},
            "geometry":{
                "type":"Point",
                "coordinates":[105.380859375,31.57853542647338]
            }
        }
    ]
}
```

## geometry属性格式

GeoJSON将所有的地理要素分为Point、MultiPoint、LineString、MultiLineString、Polygon、MultiPolygon。geometry和properties的对应关系如下：

- Point（单点要素）
```
{"type":"Feature",
    "properties":{
        "name": "要素1",
        "color": "blue",
        "material": "stone",
        "age": 15
    },
    "geometry":{
        "type":"Point",
        "coordinates":[105.380859375,31.57853542647338]
    }
}
```
- MultiPoint（多点要素）
```
{"type":"Feature",
    "properties":{
        "name": "群组1",
        "color": "blue",
        "material": "stone",
        "age": 15
    },
    "geometry":{
        "type":"MultiPoint",
        "coordinates":[
            [105.380859375,31.57853542647338],
            [105.580859375,31.52853542647338],
        ]
    }
}
```
- LineString（拟合线）
```
{"type":"Feature",
    "properties":{
        "name": "折线1",
        "color": "blue",
        "material": "stone",
        "age": 15
    },
    "geometry":{
        "type":"LineString",
        "coordinates":[[105.6005859375,30.65681556429287],
        [107.95166015624999,31.98944183792288],
        [109.3798828125,30.031055426540206],
        [107.7978515625,29.935895213372444]]
        }
    }
```
- MultiLineString（线群组）
```
{"type":"Feature",
    "properties":{
        "name": "折线组1",
        "color": "blue",
        "material": "stone",
        "age": 15
    },
    "geometry":{
        "type":"MultiLineString",
        "coordinates":
        [
            [
                [105.6005859375,30.65681556429287],
                [107.95166015624999,31.98944183792288],
                [109.3798828125,30.031055426540206],
                [107.7978515625,29.935895213372444]
            ],
            [
                [109.3798828125,30.031055426540206],
                [107.1978515625,31.235895213372444]
            ]
        ]
    }
}
```
- Polygon（多边形）
```
{"type":"Feature",
    "properties":{
        "name": "多边形1",
        "color": "blue",
        "material": "stone",
        "age": 15
    },
    "geometry":{
        "type":"Polygon",
        "coordinates":[
            [
                [106.10595703125,33.33970700424026],
                [106.32568359375,32.41706632846282],
                [108.03955078125,32.2313896627376],
                [108.25927734375,33.15594830078649],
                [106.10595703125,33.33970700424026]
            ]
        ]
    }
}
```
- MultiPolygon   
```
{
  "type": "Feature",
  "properties": {
        "name":"群组1",
        "color":"blue",
        "material":"stone",
        "age": 15
  },
  "geometry": {
  "type": "MultiPolygon",
  "coordinates":
    [ 
        [
            [
                [109.2041015625,30.088107753367257],
                [115.02685546875,30.088107753367257],
                [115.02685546875,32.7872745269555],
                [109.2041015625,32.7872745269555],
                [109.2041015625,30.088107753367257]
          
          
            ]
        ],
        [
            [
                [112.9833984375,26.82407078047018],
                [116.69677734375,26.82407078047018],
                [116.69677734375,29.036960648558267],
                [112.9833984375,29.036960648558267],
                [112.9833984375,26.82407078047018]
            ]
        ]
    ]
    }
}
```
## properties 中所含属性
```
"properties"：{
    "name":"住宅1",
    "color":"white",
    "age":15,
    "material":{
        "wall":"stone",
        "window":"woods",
        "filling":"brick"
    },
    "facility":["Tap water","electric power","natural gas"]
}
```

渲染属性与feature特征属性
- 渲染属性用于绘图如color："white"， 即使用白色绘制此feature
- feature特征属性如material和age，描述此建筑材料为石材、木材、砖块等，建筑年限为15年。

单值属性、属性集合与属性数组：
- "color":"white"
- "material":{
    "wall":"stone",
    "window":"woods",
    "filling":"brick"
}
- "facility":["Tap water","electric power","natural gas"]