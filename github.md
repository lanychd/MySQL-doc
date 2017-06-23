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

## 创建分支 
* git仓库初始化创建的时候, 会为我们自动创建一个master的主分支:git branch branch-name
* 可以从任何的地方创建分支, 并切换到新创建的分支上:git checkout -b branch-name
## 显示分支
* 显示当前git仓库中有多少个分支:git branch -av
## 分支切换
* 想从A分支切换到B分支:git checkout branch-name
## 删除分支
* 不能删除当前所在的分支:git branch -D branch-name
## 合并分支
* 将develop分支开发的提交, 合并到master分支上:
  1.git checkout master       
  2.git merge develop         
 * 出现冲突的时候可以使用mergetool, 解决冲突:git mergetool
 # 远程仓库
 ## 添加远程仓库
 * 本地有一个git仓库, 我们使用remote add 命令将它添加到远程的仓库中:git remote add origin https://github.com/lanychd/stuinfo.git
 * 将远程的仓库的信息更步到本地, 这里主要指的示远程仓库的分支和远程库的提交变更信息:git fetch origin
 ## 向远程仓库提交
 * 把本地的这次提交也要反映在远程的仓库上:git push origin master
 * 同步其它分支:git push origin branch-name
 * 将本地的tags同步(推送)到服务器上:git push origin --tags
 * 删除远程分支:git push -u origin :branch-name
 ## 从远程仓库同步
 * 将源码拉取到本地:git clone url
 * 将服务器的源码与本地源友进行同步:git pull
 # 使用github仓库
 ## github仓库的使用
 * 先在本地创建一个git仓库, 并做一个提交. 然后再互github远程仓库进行关联      
 1.echo "# abc" >> README.md       
 2.git init         
 3.git add README.md          
 3.git commit -m "first commit"         
 4.git remote add origin https://github.com/lanychd/stuinfo.git       
 5.git push -u origin master       
 * 本地已经有git仓库了, 那我们现在就直接与github仓库进行关联就可以了         
 1.git remote add origin https://github.com/lanychd/stuinfo.git       
 2.git push -u origin master       
 * 还可以用clone直接去下载这个项目, 这也是最常用下载或拉取github仓库的方法:git clone https://github.com/lanychd/stuinfo.git
