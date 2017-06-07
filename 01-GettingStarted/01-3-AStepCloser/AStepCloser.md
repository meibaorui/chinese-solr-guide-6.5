# 更进一步
对于Solr的schema你已经有了一些想法。本章节讲解Solr的主目录和其他的一些配置设置。

当Solr运行在一个应用程序服务中时，它需要能够访问主目录。主目录包含一些重要的配置信息，并且保存着Solr的索引。Solr单机模式和SolrCloud模式的主目录的目录结构会有一定程度上的不同。

Solr目录的关键部分，在以下示例中展示：
```
单机模式
<solr-home-directory>/
    solr.xml
    core_name1/
        core.properties
        conf/
            solrconfig.xml
            managed-schema
        data/
    core_name2/
        core.properties
        conf/
            solrconfig.xml
            managed-schema
        data/
```
```
SolrCloud模式
<solr-home-directory>/
    solr.xml
    core_name1/
        core.properties
        data/
    core_name2/
        core.properties
        data/
```
也许你还会看到一些其他的文件，但是这里只介绍你必须知道的那些：  
- solr.xml 用于配置你的Solr服务实例。更多关于solr.xml的信息可以查看[Solr Cores and solr.xml]()。  
- 每个Solr Core（核心）:  
    - core.properties 定义每个core的特定配置，如：他们的名字，collection属于哪个core，本地schema和其他的一些属性。关于core.properties更多的细节可以查看[定义core.properties]()。  
    - solrconfig.xml 控制高层次行为。比如你可以指定一个本地数据文件夹的替代位置。关于solrconfig.xml更多的信息可以查看[设置solrconfig.xml]()。  
    - schema.xml (或 managed-schema)用来描述你准备让solr做索引的document（文档）。这个schema将document描述为一个字段集合。你可以定义字段的类型。字段类型定义是一个强大的功能，他可以决定如何处理输入的字段值和如何检索这些值。关于Solr Schema更多的信息请查看[文档，属性，Schema设计与Schema API]().  
    - data/ 这个文件夹包含低层次的索引文件。
    
需要注意的是，对于SolrCloud来说Solr Core（核心）并不包含conf文件夹（所以也不会有solrconfig.xml和Schema文件）。这是因为conf文件夹被报错在了Zookeeper中。这样可以使得每个集群都可以获取这些信息。

如果你经常使用基于Zookeeper的SolrCloud，你可能还会看到Zookeeper的配置文件zoo.cfg和数据文件zoo.data。如果你运行你自己的Zookeeper，你会用Zookeeper的配置文件替代Solr的。更多关于Zookeeper和SolrCloud的问题可以参考[SolrCloud]()。

 