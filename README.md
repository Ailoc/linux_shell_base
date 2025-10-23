# 基础入门练习（猜数字）

```shell
#!/bin/bash

echo "欢迎进入猜数字游戏，请输入1-10中的一个数字："
num=$(shuf -i 1-10 -n 1)
echo $num

while true
do
        read guess
        if [[ $guess -eq $num ]];then
                echo "恭喜你猜对了！是否继续？（y/n）"
                read choice
                if [[ $choice = "y" ]] || [[ $choice = "Y" ]];then
                        num=$((RANDOM % 10 + 1))
                        echo $num
                        continue
                else
                        break
                fi
        elif [[ $guess -lt $number ]];then
                echo "小了！"
        else
                echo "大了"
        fi
done
```
---
- ### pwd 显示当前的目录名称
- ### ls 列出目录下的文件
        1. ls -l 显示文件的详细信息
        2. ls -a 显示隐藏的文件
        3. ls -l -r 逆向显示（按文件名）
        4. ls -l -r -t 以时间的顺序逆向显示（合并选项：ls -lrt）
        5. ls -R 递归显示文件夹中的所有文件
- ### su - root 切换为root用户
- ### cd 更改当前操作目录
        1. cd - 回到之前操作的目录
        2. cd .. 回到上一级目录
- ## 文件操作
        1. mkdir /a 在根目录下创建一个a目录
        2. mkdir a b c 在当前目录下创建三个文件夹
        3. mkdir -p a/b/c 创建多级目录
        4. rmdir /a 删除a目录，a必须为空
        5. rm -rf /a 删除非空目录
  ### 复制文件
        1. cp -r /root/a /tmp 复制a目录，-r指定复制的为目录，不指定r则为文件
        2. cp file /root 复制文件
        3. cp -p file /root 同时复制文件的操作时间
  ### 移动和重命名
        1. mv /filea /fileb 重命名。移动为不同路径，重命名为同一路径。
        2. mv /tmp/filea /fileb 移动并且重命名
        3. cp file* /tmp 复制，通配符使用，还有？通配符
- ## 文本查看
        1. cat file 文本内容显示到终端
        2. head -3 file 查看前3行
        3. tail -3 file 查看末尾3行
        4. tail -f file 内容变化时进行更新
        5. wc -l file 查看文本有多少行
        6. more file 查看文本
- ## 打包压缩和解压缩
        1. tar cf /tmp/etc/backup.tar /etc 将/etc目录打包为文件
        2. tar czf /tmp/etc/backup.tar.gz /etc 打包的同时进行压缩
        3. tar xf /tmp/etc/backup.tar -C /root 解包
        4. tar zxf /tmp/etc/backup.tar.gz -C /root 解压同时解包
- ## vim 操作
        1. vim有四种模式：正常模式、插入模式、命令模式、可视模式。
        2. 刚进入为正常模式，点击`i/a`进入插入模式，`I`在行开头插入，`A`在末尾追加，`O`在当前行上方插入一行，`o`在下方插入一行
        3. 正常模式下，`yy`复制整行，`n yy`复制连续n行，`y $`复制光标位置到当前行结尾，`p`进行粘贴
        4. 正常模式下，`dd`剪切一整行，`d $`剪切光标到行末尾, `u`进行撤销，可以多次按`u`进行多次撤销，`ctrl+r`重做
        5. 正常模式下，`x`删除一个字符，按`r+新字符`进行对旧字符的替换。`n shift+g`跳转到第n行，`gg`到第一行，`shift+g`到末尾行，`shift+6`到行开头，`shift+4`到行末尾
        6. 命令模式下，`:set nu`显示行数，`:w /root/a.txt`保存到指定位置，`:q!`不保存退出，`:!ifconfig`临时执行一条命令，`/x`查找x,`n`或`shift+n`找下一个/上一个x
        7. 命令模式下，`:s/old/new`替换当前行的字符，`:%s/old/new/g`整个进行替换，`:3,5s/old/new/g`指定区域行进行替换
        8. vim `/etc/vim/vimrc`配置文件路径
        9. v/shift+v/ctrl+v可视字符/行/块模式
- ## 用户和权限管理
        1. useradd ailoc新增用户，id ailoc查看用户，在/etc/passwd文件中可以看到，/etc/shadow保存用户密码相关文件，root用户uid为0
        2. passwd ailoc为用户设置密码，userdel ailoc删除用户(-r 同时删除相关home目录)
        3. usermod -d /home/al ailoc修改用户的home目录
        4. groupadd g1添加用户组g1，usermod -g g1 ailoc修改用户的用户组，groupdel g1删除用户组
        5. su - user1切换为user1,root授权某个命令给某个用户:visudo `user1 ALL=/sbin/shutdown -c`
