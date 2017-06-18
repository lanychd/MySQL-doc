## 创建学生信息表

```sql
 CREATE TABLE information
  (Ino CHAR(20) PRIMARY KEY,
   Iname CHAR(20) NOT NULL,
   Isex CHAR(2) CHECK (sex in ('男' ,'女')),
   Iage SMALLINT NOT NULL,
   Iphone CHAR(11) UNIQUE NOT NULL,
   Sdept CHAR(10),
   FOREIGN KEY (Sdept) REFERENCES school(Sdept)
 )character set=utf8;
```
