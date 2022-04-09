# ssh的生成
1. 打开本地终端,使用如下命令生成ssh公钥和私钥对  `ssh-keygen -t rsa -C '2542529198@qq.com'`  然后一路回车  回车然后会出现：Enter file in which to save the key (/Users/idid/.ssh/id_rsa):  这里可以输入你想定义的文件名称，也可以直接回车

2. 如果你的.ssh/id_rsa已经，则会出现：/Users/idid/.ssh/id_rsa already exists.  Overwrite (y/n)? y  输入：y  （重新覆盖）  输入：n  （不覆盖）

3. 设置你的密码(可不设)

4. 查看本机ssh公钥，并获取  `cd ~/.ssh`（进入ssh文件夹）  `ls`（查看目录是否有id_rsa.pub文件）  查看公钥：`cat id_rsa.pub`  或者  `vim id_rsa.pub`  获取到的那一大段，就是我们需要的ssh key

5. 复制公钥去github上添加即可