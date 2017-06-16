##  学生成绩信息表

```sql
CREATE TABLE  score
  (Ino CHAR(20) NOT NULL,
   Cno CHAR(20) UNIQUE NOT NULL,
   grade SMALLINT ,
   PRIMARY KEY (Ino,Cno),
   FOREIGN KEY (Ino) REFERENCES information(Ino),
   FOREIGN KEY (Cno) REFERENCES course(Cno)
   )character set=utf8;
```
