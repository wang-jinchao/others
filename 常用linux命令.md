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

#### 设置方法：  
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