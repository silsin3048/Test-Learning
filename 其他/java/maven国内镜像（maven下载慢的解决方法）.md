Maven是当前流行的项目管理工具，但官方的库在国外经常连不上，连上也下载速度很慢。国内oschina的maven服务器很早之前就关了。今天发现阿里云的一个中央仓库，亲测可用。
```
1 <mirror>
2     <id>alimaven</id>
3     <mirrorOf>central</mirrorOf>
4     <name>aliyun maven</name>
5     <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
6 </mirror>
```
　　修改${maven.home}/conf或者${user.home}/.m2文件夹下的settings.xml文件，在<mirrors>标签下加入上述内容即可。如下：
```
 1 <?xml version="1.0" encoding="UTF-8"?>
 2 <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
 3           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 4           xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
 5     <mirrors>
 6         <!-- 阿里云仓库 -->
 7         <mirror>
 8             <id>alimaven</id>
 9             <mirrorOf>central</mirrorOf>
10             <name>aliyun maven</name>
11             <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
12         </mirror>
13     
14         <!-- 中央仓库1 -->
15         <mirror>
16             <id>repo1</id>
17             <mirrorOf>central</mirrorOf>
18             <name>Human Readable Name for this Mirror.</name>
19             <url>http://repo1.maven.org/maven2/</url>
20         </mirror>
21     
22         <!-- 中央仓库2 -->
23         <mirror>
24             <id>repo2</id>
25             <mirrorOf>central</mirrorOf>
26             <name>Human Readable Name for this Mirror.</name>
27             <url>http://repo2.maven.org/maven2/</url>
28         </mirror>
29     </mirrors> 
30 </settings>
```