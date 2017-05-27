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

>![](img/info-img.png)**启动SolrCloud**：运行示例cloud要是用[SolrCloud]()模式。关于开始使用SolrCloud的云模式的更多信息请参考[开始使用SolrCloud]()章节。

#### 查看Solr已运行
如果你不确定Solr是否已运行，你可以使用status命令：
```Bash
$ bin/solr status
```
这条命令将搜索所有运行在你机器上的Solr实例，然后展示他们的基本信息，比如版本和内存使用量。

就是这样！Solr运行起来了。如果你需要进一步确认，你可以用浏览器查看管理界面。
>http://localhost:8983/solr/

![Solr管理界面](img/01-1-0.png)

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

bin/post可以将多种多样的文本发送给Solr，包括Solr原生的XML和JSON，CSV，富文本文件的文件夹，和简单的网络爬虫。查看bin/post -help结尾的示例，可以很简单的使用各种命令向Solr发送你的文档。

接着，来添加一些XML示例文件：
```Bash
$ bin/post -c gettingstarted example/exampledocs/*.xml
SimplePostTool version 5.0.0
Posting files to [base] url http://localhost:8983/solr/gettingstarted/update...
Entering auto mode. File endings considered are
xml,json,csv,pdf,doc,docx,ppt,pptx,xls,xlsx,odt,odp,ods,ott,otp,ots,rtf,htm,html,txt,log
POSTing file gb18030-example.xml (application/xml) to [base]
POSTing file hd.xml (application/xml) to [base]
POSTing file ipod_other.xml (application/xml) to [base]
POSTing file ipod_video.xml (application/xml) to [base]
POSTing file manufacturers.xml (application/xml) to [base]
POSTing file mem.xml (application/xml) to [base]
POSTing file money.xml (application/xml) to [base]
POSTing file monitor.xml (application/xml) to [base]
POSTing file monitor2.xml (application/xml) to [base]
POSTing file mp500.xml (application/xml) to [base]
POSTing file sd500.xml (application/xml) to [base]
POSTing file solr.xml (application/xml) to [base]
POSTing file utf8-example.xml (application/xml) to [base]
POSTing file vidcard.xml (application/xml) to [base]
14 files indexed.
COMMITting Solr index changes to http://localhost:8983/solr/gettingstarted/update...
Time spent: 0:00:00.153
```
就是它！Solr索引了那些文档。

## 一些问题
现在你拥有了一些被索引的文档，你可以开始检索了。最简单的方法是使用带有检索参数的URL来进行检索。这和拼接任何HTTP URL都一样。

比如检索所有包含video的文档：
>http://localhost:8983/solr/gettingstarted/select?q=video

注意构建URL的方式。这个URL包括主机名（localhost），服务监听的端口号（8983），应用的名字（solr），检索请求处理器（select），最后是检索参数（q=video）。

你可以点击上边的链接查看最终的结果。最终结果是一个XML文档。这个XML文档包括两个部分。第一部分是包含应答信息的responseHeader（应答头）。另一个返回的主要部分是result标签中的部分。这部分包含一个或多个doc标签，每个doc标签中包含匹配检索结果的文档的各种字段。你可以用标准的XML解析技术将Solr的返回结果构建为适合向用户展示的形式。同时，Solr还可以将结果输出为JSON，PHP，Ruby，甚至用户自定义的各种格式。

如果你现在不能运行Solr，下边的截图展示了这个检索在火狐浏览器中的返回结果。在响应的顶层包含一个名为responseHeader的lst标签和一个名为response的result标签。在result标签中，你可以看到三个doc标签，代表着检索结果。

![检索的XML响应](img/01-1-1.png)

一旦你掌握了检索（query）的基本思想，你就能狗自己去太多检索语句的更多功能。下边的例子和之前的检索语句类似，但是它的结果仅返回文档的id，name和price。如果你不指定你想要发挥的字段，将返回所有的字段。
>http://localhost:8983/solr/gettingstarted/select?q=video&fl=id,name,price

这里还有个仅检索name为black的例子。如果你不告诉Solr检索哪个字段，它就会检索schema中指定的默认检索字段。
>http://localhost:8983/solr/gettingstarted/select?q=name:black

你还可以对字段进行范围查询。下边这个查询意在查找所有price在$0和$400之间的所有文档。
>http://localhost:8983/solr/gettingstarted/select?q=price:[0%20TO%20400]&fl=id,name,price

[分面检索]()是Solr的关键特性之一。它可以让用户缩小检索结果，这对你的应用是一个很有意义的功能。比如，一个电商网站可以通过品牌（manufacturer）和价格（price）来缩小检索结果。

分面（facet）信息将作为检索结果的第三部分返回。你可以使用以下检索来获得这项能力。向检索中添加facet=true和facet.field=cat。
>http://localhost:8983/solr/gettingstarted/select?q=price:[0%20TO%20400]&fl=id,name,price&facet=true&facet.field=cat

除了之前的responseHeader和response标签，还显示了facet_counts标签。这里将responseHeader和response折叠起来，以便于你可以清晰的看到分面信息。

```xml
<response>
    <lst name="responseHeader">
    ...
    </lst>
    <result name="response" numFound="9" start="0">
        <doc>
            <str name="id">SOLR1000</str>
            <str name="name">Solr, the Enterprise Search Server</str>
            <float name="price">0.0</float>
        </doc>
        ...
    </result>
    <lst name="facet_counts">
        <lst name="facet_queries"/>
        <lst name="facet_fields">
            <lst name="cat">
                <int name="electronics">6</int>
                <int name="memory">3</int>
                <int name="search">2</int>
                <int name="software">2</int>
                <int name="camera">1</int>
                <int name="copier">1</int>
                <int name="multifunction printer">1</int>
                <int name="music">1</int>
                <int name="printer">1</int>
                <int name="scanner">1</int>
                <int name="connector">0</int>
                <int name="currency">0</int>
                <int name="graphics card">0</int>
                <int name="hard drive">0</int>
                <int name="monitor">0</int>
            </lst>
        </lst>
        <lst name="facet_dates"/>
        <lst name="facet_ranges"/>
    </lst>
</response>
```
分面信息中展示了cat字段的每种值在检索中的数量各有多少。你可以使用这种信息很容易的帮助用户快速的缩小检索结果。你可以添加多个过滤检索（filter query）条件发送Solr请求。这个请求中限制了文档的分类为"software"。
>http://localhost:8983/solr/gettingstarted/select?q=price:0%20TO%20400&fl=id,name,price&facet=true&facet.field=cat&fq=cat:software



