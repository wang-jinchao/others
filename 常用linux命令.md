# Linux相关

### 常用linux命令  

1. 查看磁盘大小：df
2. 查看文件大小：du -h . --max-depth=1
3. find -name ''
4. grep 'patton' file
5. cat
6. \>
7. tree -L 2
8. top  


### Linux环境变量  
#### 分类：
>一、生命周期:  
1、永久的：需要用户修改相关的配置文件，变量永久生效。  
2、临时的：用户利用export命令，在当前终端下声明环境变量，关闭Shell  终端失效。   
二、作用域:  
1、系统环境变量：系统环境变量对该系统中所有用户都有效。  
2、用户环境变量：顾名思义，这种类型的环境变量只对特定的用户有效。  

### 设置方法（PATH／LD_LIBRARY_PATH）:
##### PATH:可执行程序的查找路径  
一、在/etc/profile文件中添加变量 对所有用户生效（永久的）  
>用vim在文件/etc/profile文件中增加变量，该变量将会对Linux下所有用户有效，并且是“永久的”。  
例如：编辑/etc/profile文件，添加CLASSPATH变量 

    vim /etc/profile    
    export CLASSPATH=./JAVA_HOME/lib;$JAVA_HOME/jre/lib 
>注：修改文件后要想马上生效还要运行source /etc/profile不然只能在下次重进此用户时生效。
  
二、在用户目录下的.bash_profile文件中增加变量 【对单一用户生效（永久的）】
>用vim ~/.bash_profile文件中增加变量，改变量仅会对当前用户有效，并且是“永久的”。

    vim ~/.bash.profile
    export CLASSPATH=./JAVA_HOME/lib;$JAVA_HOME/jre/lib
>注：修改文件后要想马上生效还要运行$ source ~/.bash_profile不然只能在下次重进此用户时生效。

三、直接运行export命令定义变量 【只对当前shell（BASH）有效（临时的）】
>在shell的命令行下直接使用export 变量名=变量值
定义变量，该变量只在当前的shell（BASH）或其子shell（BASH）下是有效的，shell关闭了，变量也就失效了，再打开新shell时就没有这个变量，需要使用的话还需要重新定义。
  
##### LD_LIBRARY_PATH:动态库的查找路径   
>方法一： export  LD_LIBRARY_PATH=LD_LIBRARY_PATH:/XXX 但是登出后就失效  

>方法二：修改~/.bashrc或~/.bash_profile或系统级别的/etc/profile  
         1. 在其中添加例如export PATH=/opt/ActiveP/lib:$LD_LIBRARY_PATH  
         2. source .bashrc  (Source命令也称为“点命令”，也就是一个点符号（.）。source命令通常用于重新执行刚修改的初始化文件，使之立即生效，而不必注销并重新登录)  

>方法三：这个没有修改LD_LIBRARY_PATH但是效果是一样的实现动态库的查找,  
         1. /etc/ld.so.conf下面加一行/usr/local/mysql/lib  
         2. 保存过后ldconfig一下（ldconfig 命令的用途,主要是在默认搜寻目录(/lib和/usr/lib)以及动态库配置文件/etc/ld.so.conf内所列的目录下,搜索出可共享的动态链接库(格式如前介绍,lib*.so*),进而创建出动态装入程序(ld.so)所需的连接和缓存文件.缓存文件默认为/etc/ld.so.cache,此文件保存已排好序的动态链接库名字列表.）  
        方法三设置稍微麻烦，好处是比较不受用户的限制。