# git 源码管理  
## git 安装  
1.使用命令安装git工具； sudo apt-get install git
## 创建版本库：  
1.仓库的创建  
* 第一步, 先创建一个目录, 目录用来存放仓库: mkdir html         
       cd html    
* 第二步, 使用git init命令, 将当前目录创建成git仓库: git init   
* 第三步，查看仓库下的隐藏文件: ls -al      
2.增加文件   
* 在空目录下创建一个文件README: touch README    
* 编辑这个文件： vim README    
* 查看当前目录下文件的状态： git status   
* 把文件加仓库中： git add README   
* 再次查看当前目录下文件的状态: git status        
3. 文件的提交   
* git commit        
4. 配置用户信息    
* 配置用户名: git config --global user.name   
* 配置用户邮箱: git config --global user.email        
5. 配置编辑提交信息的编辑器： git config --global core.editor vim    
## 查看提交信息   
1. 查看提交的信息.       
* git log   
## 文件的删除和恢复   
1.删除文件  
* rm demo.md  
2.查看文件  
* ls  
3.使用git命令查看仓库的状态  
* git status  
4.若误删，恢复：     
* git checkout demo.md  
5.再次查看文件是否存在  
* ls  
6.再次查看仓库的状态  
* git status  
7.再次提交  
* git commit  
## 版本回退  
1.想回退到上次提交的版本, 那么需要使用git reset命令.       
* git reset --hard commitID  
2.再使用git log命令不会查看到所有log的相关信息, 不会获取到后一个提交的CommitID.         
* git log   
3.使用git reflog命令查看后一次提交的CommitID        
* git reflog
## 从版本库中忽略文件  
1. 在仓库中忽略垃圾文件  
* touch .gitignore    
## 版本之间对比  
1.对比版本之间看看有什么不同  
* git diff   
* git diff commitID1 commitID2   
## git生成patch  
* git format-patch -p1  
## git打包patch  
* git am patch-name  
     
