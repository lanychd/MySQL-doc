# git 源码管理    
 ## git 安装    
    
     1.使用命令安装git工具； sudo apt-get install git
     
 ## 创建版本库：     
     1.仓库的创建    
         * 第一步, 先创建一个目录, 目录用来存放仓库.    
         *mkdir html   
         *cd html    
         * 第二步, 使用git init命令, 将当前目录创建成git仓库.    
         * git init   
         * 第三步，查看仓库下的隐藏文件   
         * ls -al   
     2.增加文件   
       * 在空目录下创建一个文件README.   
       * touch README    
       * 编辑这个文件.    
       * vim README    
       * 查看当前目录下文件的状态.    
       * git status   
       * 把文件加仓库中.    
       * git add README   
       * 再次查看当前目录下文件的状态.
       * git status   
     3. 文件的提交   
       * git commit    
     4. 配置用户信息    
          * 配置用户名   
          *git config --global user.name   
          * 配置用户邮箱    
          * git config --global user.email    
     5. 配置编辑提交信息的编辑器    
          * git config --global core.editor vim    
  ## 查看提交信息   
     1. 查看提交的信息.       
        * git log   
  ## 文件的删除和恢复 
     
            
