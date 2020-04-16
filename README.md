# DCDBDump使用手册
DCDBDump是DCDB的一款命令行工具，DCDBDump属于单线程，导出兼容mysql格式的sql文件，可以用于执行导出任务。
## DCDBDump的使用
### 参数
>`-h`:指定DCDB的db所在节点的IP
>`-P`:指定DCDB中db运行的端口号
>`-u`:DCDB的用户名
>`-p`:DCDB的用户密码
>`--databases`:导出的数据库
>`--path`:导出数据的路径及文件名（必须指定文件名）
>`--tables`：导出对应表格的数据
>`--dumpsize`：操作io的数量

**完整的命令：**
``` sql
 python DCDBDump.py -P28282 -h10.10.10.xxx -uroot -proot --databases DCDB --tales table_1 --path==/tmp/talbe_1.sql --dumpsize=100000
```


#### DCDBDump的命令参数分为必填参数和可选参数：
##### 必填参数：
> **`-u -p --databases`**

##### 可选参数及默认值
> `-h`：默认情况下使用本地IP
> `-P`：默认情况下使用28282
> `--path`：默认情况下，在本地以”database.sql”格式导出文件
> `--tales`：默认情况下，导出database下所有的表
> `--dumpsize`：默认值为100000

## 注意
1. 本脚本仅支持python2的解释器。
2. 性能：在单进程，测试机器的环境下：

| 机器      |    进程数 |   速度（条/小时）   | 速度（G/小时）
| :--------: | :--------:| :------: |:----:|
| 测试机    |   1 |  35000000  |6.5|


