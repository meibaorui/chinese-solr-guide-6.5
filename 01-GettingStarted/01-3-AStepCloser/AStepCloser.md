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