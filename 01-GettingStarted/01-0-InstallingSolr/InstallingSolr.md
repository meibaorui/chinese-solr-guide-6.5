# 安装Solr
本章节描述了如何安装Solr。你可以将Solr安装在任何已经有Java运行时环境（JRE）的系统上，包括：Linux，OS X和微软的Windows。除了Windows系统的一些特殊情况以外，本章节中的说明应该适用于任何平台。

## 获取Java
你需要一个1.8或更高版本的JRE。你可以在命令行中这样检查你的Java版本：
```Bash
$ java -version
java version "1.8.0_60"
Java(TM) SE Runtime Environment (build 1.8.0_60-b27)
Java HotSpot(TM) 64-Bit Server VM (build 25.60-b23, mixed mode)
```
这个输出可能会有一些变化，但是你要确保的是最低版本的正确。我们推荐你选择最高的版本。如果你没有必要的版本，或是没有java命令，请从Oracle官网下载最新的版本：[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)。

## 安装Solr
可以从Solr官网获得Solr：[http://lucene.apache.org/solr/](http://lucene.apache.org/solr/)

如果是Linux/Unix/OSX系统，下载.tgz版本。如果是Windows系统，下载.zip版本。你先要将Solr解压到你选择的目录下。如果你需要将Solr安装于生产环境，请参考章节[在生产环境使用Solr]()。我们先从简单的来。对于Linux系统来说，解压Solr到你的本地home目录：
```Bash
$ cd ~/
$ tar zxf solr-x.y.z.tgz
```
解压之后，你可以根据[运行SOlr]()章节的说明来运行Solr。