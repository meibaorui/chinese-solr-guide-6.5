# 运行Solr
本章节介绍了如何基于简单的schema运行Solr，如何添加文档，如何运行查询。
## 启动服务
如果你安装之后还没启动Solr，你可以在bin/solr路径下启动它。
```Bash
$ bin/solr start
```
如果你时Windows系统，你可以通过bin\solr.cmd启动Solr。
```Bash
bin\solr.cmd start
```
Solr将在后台运行，监听端口8983。

当你在后台启动Solr时，脚本将等待确保Solr正确执行再返回命令行提示符。

bin/solr和bin\solr.cmd脚本允许你自定义如何启动Solr。让我们来用一些简单的例子来尝试使用bin/solr脚本吧（如果你使用的是Windows系统的bin\solr.cmd，一下的例子依然适用）：

### Solr脚本选项
bin/solr脚本拥有一些选项。
#### 帮助
来看一下如何使用Solr脚本，执行：
```Bash
$ bin/solr -help
```
对于开始命令，特定用法的说明：
```Bash
bin/solr start -help
```
#### 在前台运行solr
当Solr服务运行的时候，它有很多命令行运行在后台，特别是在Unix/Linux系统上。但是，在前台运行Solr很简单：
```Bash
$ bin/solr start -f
```
如果你是Windows系统，你可以执行：
```Bash
bin\solr.cmd start -f
```
#### 使用不同端口运行Solr
你可以使用-p属性启动Solr来改变Solr监听的端口，例如：
```Bash
$ bin/solr start -p 8984
```
#### 停止Solr
当你在前台运行Solr的时候（使用 -f），你可以使用Ctrl-c停止它。但是当你在后台运行的时候你必须使用stop命令：
```Bash
$ bin/solr stop -p 8983
```
使用关闭命令行的时候，你必须提供明确的端口号，或者使用-all参数来停止所有运行的Solr实例。 
#### 使用特定的例子启动Solr
为了帮助你学习使用Solr的关键特性，Solr还为你提供了一些示例。你可以用-e来启动这些示例。例如，使用示例"techproducts"，你可以：
```Bash
$ bin/solr -e techproducts
```
你可以使用的示例有：techproducts，dih，schemaless和cloud。关于这些示例的更多细节，你可以查看[Running with Example Configurations](https://cwiki.apache.org/confluence/display/solr/Solr+Control+Script+Reference#SolrControlScriptReference-RunningwithExampleConfigurations)。

>![](../img/info-img.png)**启动SolrCloud**：运行示例cloud要是用[SolrCloud]()模式。关于开始使用SolrCloud的云模式的更多信息请参考[开始使用SolrCloud]()章节。

#### 查看Solr已运行
如果你不确定Solr是否已运行，你可以使用status命令：
```Bash
$ bin/solr status
```
这条命令将搜索所有运行在你机器上的Solr实例，然后展示他们的基本信息，比如版本和内存使用量。

就是这样！Solr运行起来了。如果你需要进一步确认，你可以用浏览器查看管理界面。
>http://localhost:8983/solr/

![](../img/01-1-0.png)

Solr管理界面

如果Solr没有启动，你的浏览器会告诉你他不能链接到服务。检查你的端口号，然后再试一遍。

## 创建核心
如果你不用示例启动Solr，你需要创建一个核心（core）来做索引和检索。你可以这样做：
```Bash
$ bin/solr create -c <name>
```
这样会创建一个核心（core）。这个核心将使用数据驱动的schema来在你添加文档去索引时推测出正确的字段类型。

查看创建一个新核心时所有可用的选项，可以执行：
```Bash
$ bin/solr create -help
```
## 添加文档（document）
Solr用于查找匹配查询的文档。Solr的schema提供了一种文本结构化的方案（稍后回介绍更多关于schema的内容），但是没有文档，那就没什么可查的。需要先输入信息给Solr，它才能干更多的事情。

在对文本建立索引前，你需要先添加一些简单的文档。Solr在安装的时候已经提供了很多不同的示例文档。在安装路径的example文件夹下可以找到这些文档。

在bin目录下有个post脚本，这是一个用于索引各类不同文档的命令行工具。现在先不用关心太多细节。在[索引和基本数据操作]()章节将会讲解更多关于索引的细节。

查看bin/post相关的信息，可以使用-help选项。Windows用户请查看[Post Tool on Windows](https://cwiki.apache.org/confluence/display/solr/Post+Tool#PostTool-WindowsSupport)。