```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <mysql/mysql.h>
#include "cgic.h"

	char * headname = "head.html";
	char * footname = "footer.html";

	int cgiMain()
	{



			FILE * fd;
			char ch;

			fprintf(cgiOut, "Content-type:text/html;charset=utf-8\n\n");
			if(!(fd = fopen(headname, "r"))){
			 fprintf(cgiOut, "Cannot open file, %s\n", headname);
			 return -1;
			}
			ch = fgetc(fd);

			while(ch != EOF){
			 fprintf(cgiOut, "%c", ch);
			 ch = fgetc(fd);
			}
			fclose(fd);
	//fprintf(cgiOut, "Content-type:text/html;charset=utf-8\n\n");

  char Ino[20] = "\0";
	char Cno[4] = "\0";
	char grade[4] = "\0";
	int status = 0;

  status = cgiFormString("Ino",  Ino, 20);
	if (status != cgiFormSuccess)
	{
		fprintf(cgiOut, "get Ino error!\n");
		return 1;
	}

	status = cgiFormString("Cno",  Cno, 4);
	if (status != cgiFormSuccess)
	{
		fprintf(cgiOut, "get Cno error!\n");
		return 1;
	}

	status = cgiFormString("grade",  grade, 4);
	if (status != cgiFormSuccess)
	{
		fprintf(cgiOut, "get grade error!\n");
		return 1;
	}

	//fprintf(cgiOut, "name = %s, age = %s, stuId = %s\n", name, age, stuId);

	int ret;
	char sql[128] = "\0";
	MYSQL *db;

	//初始化
	db = mysql_init(NULL);
	mysql_options(db,MYSQL_SET_CHARSET_NAME,"utf8");
	if (db == NULL)
	{
		fprintf(cgiOut,"mysql_init fail:%s\n", mysql_error(db));
		return -1;
	}

	//连接数据库
	db = mysql_real_connect(db, "127.0.0.1", "root", "123456", "stu",  3306, NULL, 0);
	if (db == NULL)
	{
		fprintf(cgiOut,"mysql_real_connect fail:%s\n", mysql_error(db));
		mysql_close(db);
		return -1;
	}


	sprintf(sql, "update score set grade=%d where Ino='%s'and Cno='%s'",atoi(grade),Ino,Cno);

//fprintf(cgiOut,  "%s<hr>", sql);


	if ((ret = mysql_real_query(db, sql, strlen(sql) + 1)) != 0)
	{
		fprintf(cgiOut,"mysql_real_query fail:%s\n", mysql_error(db));
		mysql_close(db);
		return -1;
	}



	fprintf(cgiOut, "update student ok!\n");
	mysql_close(db);
	return 0;
}
```
