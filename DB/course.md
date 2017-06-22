## 学生课程信息表

```sql
CREATE TABLE course
  (Cno CHAR(4) PRIMARY KEY,
   Cname CHAR(20) UNIQUE NOT NULL,
   Ccredit SMALLINT NOT NULL
   )character set=utf8;
```
