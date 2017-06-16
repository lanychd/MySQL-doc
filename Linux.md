# Linux 基本命令的使用      

## vim 基本使用       
1. 快捷键的使用：     
    i：在当前字符的左边插入     
    I：在当前行首插入     
    a：在当前字符的右边插入     
    A：在当前行尾插入     
    o：在当前行下面插入一个新行      
    O：在当前行上面插入一个新行    
    h: 向前移动一个字符   
    j: 向下移动一行     
    k: 向上移动一行     
    l: 向后移动一个字符      
    yy: 复制当前一行    
    dd:剪切当前一行     
    p: 粘贴内容到游标之后     
    P: 粘贴内容到游标之前     
    u: 恢复      
    
## 文件的基本操作     
     1.创建一个目录： mkdir dir      
     2.删除一个目录： rm -rf dir     
     3.打开一个目录： cd dir      
     4.查看目录下的文件： ls     
     5.查看目录下文件的详细信息： ls -al      
     6.查看目录下文件的隐藏文件： ls -a    
     7.创建一个文件：touch file      
     8.删除一个文件：rm -rf file     
     9.目录下查找文件：find  ./dir  -name  "filename"      
     
 ## 文件的压缩和解压      
    1.使用gzip和gunzip对文件进行压缩和解压缩      
      gzip  filename    
      gunzip filename      
    2.使用bzip2和bunzip2对文件进行压缩和解压缩    
      bzip2  filename      
      bunzip2  filename    
    3.使用tar对文件和目录进行压缩和解压缩     
      tar czvf  file.tar.gz dir     
      tar xvf  file.tar.gz    

     

      
         
