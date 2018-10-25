# 视图转换成表

```sql
// https://blog.csdn.net/xxd851116/article/details/5950321
oracle :
create table tablename as select * from viewname

sqlserver:
select * into tablename from viewname 
```

## 1. 顶部菜单栏-文件-新建-使用当前连接的查询

![](image/2018-10-25-16-59-51.png)

## 2. 编写-执行

```sql
--sqlserver--
--刚刚创建的视图可能会不提示补全，请尝试--
--重新打开sql客户端--
--检查第一步中选择‘使用当前连接的查询’，而不是‘数据库引擎查询’--
select * into result_table from my_view
```

![](image/2018-10-25-17-02-04.png)

## 3. 右键点击表-刷新-查看结果

![](image/2018-10-25-17-07-24.png)

![](image/2018-10-25-17-07-41.png)

![](image/2018-10-25-17-11-51.png)

### Author Xuekui,Zengjianjun

### Software

1. sql server 2014
2. windows server 2008r1
3. windows office 2016

### License 知识共享许可协议

本作品采用知识共享署名-非商业性使用 4.0 国际许可协议进行许可。