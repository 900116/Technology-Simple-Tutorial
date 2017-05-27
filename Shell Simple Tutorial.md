##Shell简单教程

### echo
```
#! /bin/bash
echo "Hello World !"
```
### 如果运行shell文件
终端输入  
`sh 脚本的文件名.sh`

### 变量
```
# 定义变量
# 注意：等号两边不能有空格，否则会识别成指令
variable="some value"
# 让变量只读
readonly variable
# 删除变量
unset variable_name
# 使用变量（前面需要加美元符号）
echo $variable
echo $(variable)
```

### 脚本参数
传递参数：  
在终端输入  
`sh 脚本的文件名.sh 参数1 参数2 参数3`

```
# 获取第0个参数
param1=$0 
# 获取参数个数
args_count=$#
# 获取所有参数 "参数1 参数2 参数3"表示
args=$*
# 获取所有参数 "参数1" "参数2" "参数3"表示
args2=$@
# 显示当前进程ID
pid=$$
# 后台运行的最后一个ID号
last_pid=$!
# 显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误
exit_state=$?
```

### if
注意必须以`fi`结尾

```
# if
if condition
then
    command
fi

# if - else
if condition
then
    command
else
    command
fi

# if - elif - else
if condition1
then
    command1
elif condition2 
then 
    command2
else
    commandN
fi
```

### for
```
for var in item1 item2 ... itemN
do
    command
done
#写成一行
for var in item1 item2 ... itemN; do command;done;

### 
```

### while
```
while condition
do
    command
done
```

### until
与`while`相反  

```
until condition
do
    command
done
```

### case
必须以`esac`结尾每个分支有两个分号，`*)`表示不匹配的分支

```
case $aNum in
    1)  echo '你选择了 1'
    ;;
    2)  echo '你选择了 2'
    ;;
    3)  echo '你选择了 3'
    ;;
    4)  echo '你选择了 4'
    ;;
    *)  echo '你没有输入 1 到 4 之间的数字'
    ;;
esac
```

### shell支持break和continue

### 函数
```
funWithReturn(){
    read aNum
    read anotherNum
    return $(($aNum+$anotherNum))
}
```
### 函数获取参数的方法与脚本获取参数方法一致

### 引入其他脚本
使用`.`符号引入其他sh脚本
```
. ./test1.sh
# 或者使用source
source ./test1.sh
```

### 字符串
```
# 字符串插值 
echo "${variable}"
# 字符串长度
length=${#variable}
# 子串
echo ${string:1:4}
# 字符串拼接
variable ="hello, "$your_name" !"
echo $greeting $variable
# 字符串可以使用单引号
# 单引号的字符串无法插值，并且无法用转义字符
```

### 数组
```
# 定义数组
array_name=(value0 value1 value2 value3)
# 数组赋值
array_name[0]=value0
# 数组长度
length=${#array_name[0]}
# 获取数组所有元素
echo "${my_array[*]}"
echo "${my_array[@]}"
```

### 关系运算符
算数运算符

- `+`,`-`,`*`,`/`,`%`,`=`,`==`,`!=`

关系运算符

- `-eq` 相等？
- `-ne` 不等？
- `-gt` 大于？
- `-lt` 小于？
- `-ge` 大于等于？
- `-le` 小于等于？

布尔运算符

- `!` 非
- `-o` 或
- `-a` 与

逻辑运算符

- `&&` 逻辑与
- `||` 逻辑或

字符串运算符

- `=` 相等？
- `!=` 不等？
- `-z $str` 长度为0？
- `-n $str` 长度不为0？
- `$str` 为空？

文件测试运算符

- `-d $file` 目录？
- `-f $file` 普通文件？
- `-r $file` 可读？
- `-w $file` 可写？
- `-x $file` 可执行？
- `-s $file` 0字节？
- `-e $file` 是否存在


### Shell重定向
- `command > file` 将输出重定向到file
- `command < file` 将输入重定向到file
- `command >> file` 将输出追加到file
- `n > file` 将文件描述符为 n 的文件重定向到 file
- `n >> file` 将文件描述符为 n 的文件以追加的方式重定向到 file
- `n >& file` 将输出文件 m 和 n 合并
- `n <& file` 将输入文件 m 和 n 合并
- `<< tag` 将开始标记 tag 和结束标记 tag 之间的内容作为输入


更多命令参考  
>> http://www.runoob.com/linux/linux-command-manual.html
