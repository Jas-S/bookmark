・[mysqldump只导出表结构或只导出数据的实现方法](https://www.jb51.net/article/28855.htm)

・[mysql修改表、字段、库的字符集](http://fatkun.com/2011/05/mysql-alter-charset.html)

·[set autocommit=0和start transaction的区别](https://www.jianshu.com/p/a4b22ea57186)

·[HikariCP监控指标介绍和应用](https://www.cnblogs.com/fireround/p/11756087.html)


# 命令语句
## 表狀態信息查詢
```mysql
show table status where name = 'table_name';
```
## 表结构信息查詢
```mysql
desc table;
```

## 查询表创建时间
```mysql
SELECT table_name,create_time FROM  information_schema.TABLES where TABLE_SCHEMA = 'DB名';
```

## 查看表生成的DDL
```mysql
show create table table_name;
```
## 存储过程
```mysql
drop procedure if exists `insertDate`;
delimiter //
create procedure insertDate()
begin
 declare n int default 0;
 declare days int default 0;
 set days = day(LAST_DAY(now()));
 while n < days do
   if n != 0 then
     insert into `facilityServiceDB`.`dynamic_date` (`check_in_date`) value (date_add(now(), interval n day));
   end if;
   set n = n + 1;
 end while;
end;//
delimiter ;

call insertDate();
```
