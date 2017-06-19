use stu;
CREATE TABLE information
  (Ino CHAR(20) PRIMARY KEY,
   Iname CHAR(20) NOT NULL,
   Isex CHAR(2) CHECK (sex in ('男' ,'女')),
   Iage SMALLINT NOT NULL,
   Iphone  INT UNIQUE NOT NULL,
   Sdept INT,
   FOREIGN KEY (Sdept) REFERENCES school(Sdept)
 )character set=utf8;

 CREATE TABLE school
 (Sname CHAR(20)  NOT NULL,
  Sdept  INT PRIMARY KEY,
  Sdname CHAR(20) UNIQUE NOT NULL
  )character set=utf8;
  
  CREATE TABLE course
  (Cno CHAR(4) PRIMARY KEY,
   Cname CHAR(20) UNIQUE NOT NULL,
   Ccredit SMALLINT check(Ccredit>=0 and Ccredit<=10),
   Cpno CHAR(20) /*先修课*/
   )character set=utf8;
 
 CREATE TABLE  score
  (Ino CHAR(20) NOT NULL,
   Cno CHAR(20) UNIQUE NOT NULL,
   grade SMALLINT check(grade>=0 and grade<=100),
   PRIMARY KEY (Ino,Cno),
   FOREIGN KEY (Ino) REFERENCES information(Ino),
   FOREIGN KEY (Cno) REFERENCES course(Cno)
   )character set=utf8;
   
INSERT INTO `school` (`Sname`, `Sdept`, `Sdname`) VALUES ('河北地质大学', '01', '外国语');
INSERT INTO `school` (`Sname`, `Sdept`, `Sdname`) VALUES ('河北地质大学', '02', '会计');
INSERT INTO `school` (`Sname`, `Sdept`, `Sdname`) VALUES ('河北地质大学', '03', '数理');
INSERT INTO `school` (`Sname`, `Sdept`, `Sdname`) VALUES ('河北地质大学', '04', '信息工程');

INSERT INTO `information` (`Sname`, `Sdept`, `Sdname`) VALUES ('河北地质大学', '01', '外国语');
