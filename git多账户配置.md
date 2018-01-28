1. 生成SSH Key【主账户、附账户】

 ```cmd
    $ cd .ssh
    $ ssh-keygen -t xx_rsa -C "xx@email.com"
       
    $Enter file in which to save the key (/c/Users/xx/.ssh/xx_rsa): github //可以重命名为github，方便区分
       
    $ ssh-keygen -t xx2_rsa -C "workemail@email.com"
       
    $Enter file in which to save the key (/c/Users/xx/.ssh/xx2_rsa): work
    
        ... 后续直接回车到完成。
        
 ```
> github 经常用的设置为主账户
> work 不常用的设置为附账户


2. 配置config文件
    
    ```cmd
        
    cd ~/.ssh   // 进入ssh目录
    ls           //查看文件
    touch config  //且添加如下下内容【如果有省略】
    ```
    
    config 内容如下
    
    ```cmd
    #主账户
    Host github.com       //这个我就保持与HostName一致了
    HostName github.com   //对应仓库的站点
    User name               //用户名
    IdentityFile  ~/.ssh/github  //对应的ssh key 文件
    #附属账户
    Host work.com
    HostName work.com
    User name
    IdentityFile  ~/.ssh/work 
            
    ```
3. clone 使用
    
    ```cmd
    
    当我们正常去clone代码的时候，给出的地址会是
    
    git clone git@github.com:xx/project1.git
     
    git clone git@work.com:xx/project2.git
      
    eg:
    github clone地址如:
    git@github.com:JonyShiw/react-native-webstrom.git
    
    1、主账户直接使用地址即可。
    2、附账户
    git@work.com:JonyShiw/react-native-webstrom.git
    
    
    ```cmd
    
3. github 其他命令
    
    ```cmd
    
    1、把专用密钥添加到 ssh-agent 的高速缓存中： 
        ssh-add ~/.ssh/id_dsa 
        
    2、从ssh-agent中删除密钥： 
        ssh-add -d ~/.ssh/id_xxx.pub 
        
    3、查看ssh-agent中的密钥： 
        ssh-add -l
     
     
    -D：删除ssh-agent中的所有密钥. 
    -d：从ssh-agent中的删除密钥 
    -e pkcs11：删除PKCS#11共享库pkcs1提供的钥匙。 
    -s pkcs11：添加PKCS#11共享库pkcs1提供的钥匙。 
    -L：显示ssh-agent中的公钥 
    -l：显示ssh-agent中的密钥 
    -t life：对加载的密钥设置超时时间，超时ssh-agent将自动卸载密钥 
    -X：对ssh-agent进行解锁 
    -x：对ssh-agent进行加锁
    ```


