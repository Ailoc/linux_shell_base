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
        1. mv /filea /fileb 重命名
        2. mv /tmp/filea /fileb 移动并且重命名
        3. cp file* /tmp 复制，通配符使用，还有？通配符 
