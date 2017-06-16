## 学生成绩信息表

```sql
CREATE TABLE course
  (Cno CHAR(4) PRIMARY KEY,
   Cname CHAR(20) UNIQUE NOT NULL,
   Ccredit SMALLINT NOT NULL,
   Cpno CHAR(20) /*先修课*/
   )character set=utf8;
```
