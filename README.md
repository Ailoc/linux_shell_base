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

