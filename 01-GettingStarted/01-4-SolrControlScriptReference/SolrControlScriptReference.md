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
start命令用于启动Solr。在Solr启动或是已经停止的情况下，你可以使用restart命令重启Solr。

start和restart还拥有一些选项可以让你使用SolrCloud的模式启动，选择配置文件，设置非默认的端口号和指定本地zookeeper。

```bash
bin/solr start [options]
bin/solr start -help
bin/solr restart [option]
bin/solr restart -help
```

当你使用restart命令的时候，你必须将所有你启动时传递的参数再次传递。因为本质上来讲，在使用restart的时候，就是先发送了一个stop命令，Solr停止之后再进行启动。如果没有正在启动的节点，restart将跳过stop过程直接启动Solr。

### 可用的参数
bin/solr脚本提供了很多种设置来帮助你自定义Solr服务，比如更改监听端口。虽然，默认设置其实对大多数人来说都是够用的，尤其是对于刚开始使用的人来说。

参数| 描述| 示例
-------|-------|-------
-a "<string>" | 启动Solr时添加JVM参数，比如启动时使用-X。如果你以-D开头传递JVM参数，则可以省略-a。| bin/solr start -a "-Xdebug -Xrunjdwp:transport=dt_socket,server=y,supend=n,address=1044" 