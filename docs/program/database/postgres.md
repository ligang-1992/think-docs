#### PostGIS教程:几何图形（geometry）

```
ST_Area: Returns the area of the surface if it is a polygon or multi-polygon. For “geometry” type area is in SRID units. For “geography” area is in square meters.

ST_AsText: Returns the Well-Known Text (WKT) representation of the geometry/geography without SRID metadata.

ST_AsBinary: Returns the Well-Known Binary (WKB) representation of the geometry/geography without SRID meta data.

ST_EndPoint: Returns the last point of a LINESTRING geometry as a POINT.

ST_AsEWKB: Returns the Well-Known Binary (WKB) representation of the geometry with SRID meta data.

ST_AsEWKT: Returns the Well-Known Text (WKT) representation of the geometry with SRID meta data.

ST_AsGeoJSON: Returns the geometry as a GeoJSON element.

ST_AsGML: Returns the geometry as a GML version 2 or 3 element.

ST_AsKML: Returns the geometry as a KML element. Several variants. Default version=2, default precision=15.

ST_AsSVG: Returns a Geometry in SVG path data given a geometry or geography object.

ST_ExteriorRing: Returns a line string representing the exterior ring of the POLYGON geometry. Return NULL if the geometry is not a polygon. Will not work with MULTIPOLYGON

ST_GeometryN: Returns the 1-based Nth geometry if the geometry is a GEOMETRYCOLLECTION, MULTIPOINT, MULTILINESTRING, MULTICURVE or MULTIPOLYGON. Otherwise, return NULL.

ST_GeomFromGML: Takes as input GML representation of geometry and outputs a PostGIS geometry object.

ST_GeomFromKML: Takes as input KML representation of geometry and outputs a PostGIS geometry object

ST_GeomFromText: Returns a specified ST_Geometry value from Well-Known Text representation (WKT).

ST_GeomFromWKB: Creates a geometry instance from a Well-Known Binary geometry representation (WKB) and optional SRID.

ST_GeometryType: Returns the geometry type of the ST_Geometry value.

ST_InteriorRingN: Returns the Nth interior linestring ring of the polygon geometry. Return NULL if the geometry is not a polygon or the given N is out of range.

ST_Length: Returns the 2d length of the geometry if it is a linestring or multilinestring. geometry are in units of spatial reference and geography are in meters (default spheroid)

ST_NDims: Returns coordinate dimension of the geometry as a small int. Values are: 2,3 or 4.

ST_NPoints: Returns the number of points (vertexes) in a geometry.

ST_NRings: If the geometry is a polygon or multi-polygon returns the number of rings.

ST_NumGeometries: If geometry is a GEOMETRYCOLLECTION (or MULTI*) returns the number of geometries, otherwise return NULL.

ST_Perimeter: Returns the length measurement of the boundary of an ST_Surface or ST_MultiSurface value. (Polygon, Multipolygon)

ST_SRID: Returns the spatial reference identifier for the ST_Geometry as defined in spatial_ref_sys table.

ST_StartPoint: Returns the first point of a LINESTRING geometry as a POINT.

ST_X: Returns the X coordinate of the point, or NULL if not available. Input must be a point.

ST_Y: Returns the Y coordinate of the point, or NULL if not available. Input must be a point.
————————————————
版权声明：本文为CSDN博主「zhangkaixuan456」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/zhangkaixuan456/article/details/121275736
```



#### PostgreSQL–常用字符串函数与操作符

```
第一类：字符串连接

函数：string || string
说明：字符串连接
示例：select ‘Postgre’ || ‘SQL’;
结果：PostgreSQL

函数：string || non-string
说明：字符串与非字符串类型进行连接
示例：select ‘PostgreSQL’ || 123; –与select ‘PostgreSQL’ || 123::text; 效果相同
结果：PostgreSQL123

第二类：获取长度与位置

函数：length(string) or char_length(string) or character_length(string)
说明：获取字符串中字符个数
示例：select length(‘PostgreSQL’);
结果：10

函数：bit_length(string)
说明：获取字符串的位数
示例：select bit_length(‘PostgreSQL’);
结果：80

函数：octet_length(string)
说明：获取字符串的字节数
示例：select octet_length(‘中国人’);
结果：9

函数：position(substring in string)
说明：获取子字串的位置
示例：select position(‘gre’ in ‘PostgreSQL’);
结果：5

第三类：字符串转化

函数：upper(string)
说明：转大写
示例：select upper(‘PostgreSQL’);
结果：POSTGRESQL

函数：lower(string)
说明：转小写
示例：select upper(‘PostgreSQL’);
结果：postgresql

函数：md5(string)
说明：md5编码
示例：select md5(‘PostgreSQL’);
结果：399bd1ee587245ecac6f39beaa99886f

函数：hashbpchar(string)
说明：hash编码
示例：select hashbpchar(‘PostgreSQL’);
结果：521680097

函数：to_hex(number int 或者 bigint)
说明：转换为十六进制
示例：select to_hex(1234567890);
结果：499602d2

函数：quote_ident(string text)
说明：返回给出字串的一个适用于在SQL语句字串里当作标识符引起使用的形式。
示例：select quote_ident(‘abcd’);
结果：”abcd”

函数：quote_literal(string text)
说明：返回给出字串的一个适用于在SQL语句字串里当作文本使用的形式。
示例：select quote_literal(‘abc\d’);
结果：E’abc\d’

函数：trim(string)
说明：删除字符串string两边空格
示例：select length(trim(’ Postgre SQL ‘));
结果：10
备注：ltrim 和 rtirm 分别是删除左边和右边空格

第四类：字符串替换

函数：replace(string text, from text, to text)
说明：字符串替换，即把字串string里出现地所有子字串 from 替换成子字串 to
示例：select replace(‘abcXXabcXXdef’, ‘XX’, ‘|’);
结果：abc|abc|def

函数：translate(string text, from text, to text)
说明：字符串替换，把在 string 中包含的任何匹配 from 中的字符的字符转化为对应的 在 to 中的字符
示例：select translate(‘abcXXabcXXdef’, ‘XX’, ‘|’);
结果：abc||abc||def
备注：注意replace 与 translate 的区别

函数：overlay(string placing string from int [for int])
说明：字符串替换，即把字串string里出现地所有子字串 from 替换成子字串 to
示例：select overlay(‘Txxxxas’ placing ‘hom’ from 2 for 4); –注意与select overlay(‘Txxxxas’ placing ‘hom’ from 2 )区别;
结果：Thomas

第五类：字符串提取

函数：split_part(string text, delimiter text, fieldint)
说明：字符串提取 ，根据 delimiter 分隔 string 返回生成的第 field 个子字串（一为基）
示例：select split_part(‘abc|123|def’,’|’,3);
结果：def

函数：substr(string, from [, count])
说明：字符串提取 ，从string 以from开始 抽取count个字符串（若count没有，则以from开始 后面全部字符串）
示例：select substr(‘abc1234def’, 4, 3);
结果：123
————————————————
版权声明：本文为CSDN博主「weixin_43047710」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weixin_43047710/article/details/82186801
```



#### PostgreSQL

##### 安装

###### 步骤一：拉取镜像

```shell
~ % docker pull postgres
```

###### 步骤二：创建容器

```shell
~ % docker run -d \
    --name postgres \
    -p 5432:5432 \
    -e POSTGRES_USER=root \
    -e POSTGRES_PASSWORD=123456 \
    -e TZ=PRC \
    -e PGDATA=/var/lib/postgresql/data/pgdata \
    -v $PWD/devtools/docker/postgres:/var/lib/postgresql/data \
    postgres:14.0
```

更新时间：2020-03-21



#### SpringBoot 连接 Postgresql 指定模式Schema

一般的连接方式，我们创建数据库之后，在public 的Schema（模式）下建表，这时使用连接方式

```
jdbc:postgresql://localhost:5432/postgresql
在这种连接方式下，默认连接使用的是postgesql数据库的`public`模式
```

在业务场景中有时允许多个用户使用一个数据库并且不会互相干扰。这时需要在使用同一个数据库 新建其他模式进行连接。这时在springboot的数据源jdbc配置时注意。

```
postgresql-> 9.3 及以前的版本指定方式
spring.datasource.url=jdbc:postgresql://localhost:5432/postgresql?searchpath=new_schema

postgresql-> 9.4 及以后的版本指定方式
spring.datasource.url=jdbc:postgresql://localhost:5432/postgresql?currentSchema=new_schema
```



#### Postgresql自动生成ID

```
select sys_guid();
```

