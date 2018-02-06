# 数据库相关

## 一、检索数据  

1. 检索不同的值  
`select vend_id from Products group by vend_id`或者`SELECT DISTINCT vend_id FROM Products;`  
结果一直，但一般都用`distinct`去重，性能更高。*不能部分使用distinct，作用于所有检索列*  

2. 限制结果  
只想返回第一行或者一定数量的行时，各数据库的sql实现不一致：  
- SQL Server和Access中使用`TOP`限制返回多少行（`SELECT TOP 5 prod_name FROM Products;`检索前5行）；  
- DB2 
