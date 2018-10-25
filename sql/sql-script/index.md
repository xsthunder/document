[sql server functions](https://docs.microsoft.com/zh-cn/sql/t-sql/functions/cast-and-convert-transact-sql?view=sql-server-2017#BKMK_examples)

[sql server create xml](
    https://docs.microsoft.com/zh-cn/sql/relational-databases/xml/create-instances-of-xml-data?view=sql-server-2017
)

```sql
use test  
declare @xml xml;
set @xml =  '<hello>
<how>
abc
</how>
</hello>'
insert into 
	test(住院号,病例内容)
values ('0870-2', @xml)
go
```