# Apache Solr参考指南
本参考指南描述了搜索开源解决方案Solr。你可以通过网站 [http://lucene.apache.org/solr/](http://lucene.apache.org/solr/) 下载Apache Solr。  
本指南包含以下几个部分：  
**[准备开始](/01-GettingStarted/GettingStarted.md)**：本小节将指导你安装及启动Solr。  

**使用Solr管理用户界面**：本部分将介绍Solr基于web的用户界面。通过你的浏览器你可以查看配置稳健，提交检索，查看日志和java环境配置，监控和控制分布式配置。  

**文档，属性和Schema设计**：本部分介绍Solr如何组织它的数据索引。还介绍了Solr如何通过schema定义用于在索引中组织文档数据的字段和字段类型。  

**理解分析器（Analyzers）,分词器（Tokenizers）和过滤器（Filter）**：本部分介绍Solr如何为索引和检索准备文本。解析器解析并生成用于索引和检索的词汇流与词语单元。分词器将每个字段分解为词汇。过滤器对词汇流做一些其他的替换或筛选工作。  

**索引与基础数据操作**：本部分介绍索引过程与基本的索引操作，比如提交，优化与回退。

**检索**：本部分介绍Solr检索过程的概况。本部分描述了检索的主要组件，包括请求处理器，查询解析器和响应写入器。列举了可以发送给Solr的参数。介绍了可以用于检索结果微调的一些机制，例如权重（boost）和分面（facet）。

**Solr实例配置优化**:本部分讨论了Solr性能优化，先介绍了solrconfig.xml的概述，然后告诉你如何配置核心的solr.xml，如何配置Lucene的索引器，等等。

**管理Solr**：本部分讨论了关于运行和监控Solr的重要主题。还有一些其他的主题，比如如何备份Solr实例，如何在JMX上运行Solr。

**SolrCloud**：本部分介绍了最新最激动人心的SolrCloud。SolrCloud提供了分布式机制。

**伸缩和分布式**:本章节告诉你使用将大索引切分到多个服务器的多个shards上或复制单个索引到多个服务器来增强Solr的分布式能力。

**客户端API**:本章节告诉你如何通过JavaScript，JSON，Ruby等不同的客户端API来访问Solr。
