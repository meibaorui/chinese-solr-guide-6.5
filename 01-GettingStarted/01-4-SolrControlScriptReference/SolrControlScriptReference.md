# Solr脚本参考

bin/solr脚本可以让你启动或停止Solr，创建或删除collection或core，执行Zookeeper上的设置，检查Solr状态，配置shards（分片）。你可以在Solr安装路径的bin文件夹下找到这个脚本。bin/solr脚本提供了简单的命令行和一些选项，使你能够快速简单的完成一些目标。

下边的标题与命令行互相对应。每一个命令的选项都将给出描述和事例。

更多的使用事例可以参见[运行Solr](01-GettingStarted/01-1-RunningSolr/RunningSolr.md)章节和[开始使用Solr云]()章节。

* [启动和停止](#启动和停止)
    * [启动和重启](#启动和重启)
    * [停止]()
* [系统信息]()
    * [版本]()
    * [状态]()
    * [Healthcheck]()
* [Collection和Core]()
    * [创建]()
    * [删除]()
* [zookeeper设置]()
    * [上传配置文件]()
    * [下载配置文件]()
    * [在本地与zookeeper之间复制文件]()
    * [移除zookeeper节点]()
    * [移动一个zookeeper节点到另一个（重命名）]()
    * [列出zookeeper节点的子节点]()
    * [创建节点（提供根目录）]()
    
# 启动和停止
## 启动和重启
