# DCDBDump使用手册
DCDBDump是DCDB的一款命令行工具，DCDBDump属于单线程，导出兼容mysql格式的sql文件，可以用于执行导出任务。
## DCDBDump的使用
### 参数
>`-h`:指定DCDB的db所在节点的IP
>`-P`:指定DCDB中db运行的端口号
>`-u`:DCDB的用户名
>`-p`:DCDB的用户密码
>`--databases`:导出的数据库
>`--path=`:导出数据所在的路径及文件名（必须指定文件名）
>`--tables`：导出对应表的数据（可以指定多个表）

**完整的命令：**
```python
 python DCDBDump.py -P28282 -h10.10.10.xxx -uroot -proot --databases DCDB --tales table_1 table_2 --path=/tmp/talbe_1.sql
```


#### DCDBDump的命令参数分为必填参数和可选参数：
##### 必填参数：
> **`-u -p --databases`**

必填参数为要使用DCDBDump导出数据，最少指定的参数个数，下面的命令为DCDBdump最短指令：

```python
python DCDBDump.py -uroot -proot --databases DCDB
```

##### 可选参数及默认值
> `-h`：默认情况下使用本地IP
> `-P`：默认情况下使用28282
> `--path`：默认情况下，在本目录下保存导出数据
> `--tales`：默认情况下，导出database下所有的表（所有表中的数据都导出到databases.sql文件下）

默认值为当不指定此参数，参数使用的默认值，一旦指定参数，必须填写参数值。
```python
# 使用本地ip，port为28282，导出DCDB所有表的数据保存在本目录下DCDB.sql文件中
python DCDBDump.py -uroot -proot --databases DCDB
```

## 注意
1. 本脚本仅支持python2的解释器。
2. 服务器必须安装pymysql 库
3. 导出文件里只含有数据，不含有除数据外的其他数据库操作语句
4. DCDBDump 只能用在能正常访问DCDB的服务器上
5. 性能：在单进程，测试机器的环境下：
表的规格为：

```powershell
`id` bigint(20) 
`git_url` varchar(1024) 
`create_time` bigint(20) 
`operator` varchar(1024) 
`git_ssh_url` varchar(1024) 
`log` varchar(1024) 
`status` varchar(1024) 
```

| 机器      |    进程数 |   速度（条/小时）   | 速度（G/小时）
| :--------: | :--------:| :------: |:----:|
| 测试机    |   1 |  35000000  |6.5|


