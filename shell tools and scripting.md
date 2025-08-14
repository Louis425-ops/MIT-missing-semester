- **shell tools and scripting**

double quotes with a `$` will replace a string , while single quotes won't

```bash
vim  mcd.sh
// it use vim to open a file name mcd.sh, if not exist, create it
source mcd.sh
// 可以直接在原来的shell中执行脚本中的命令
mcd test
// mcd 是在mcd.sh中定义的函数, 通过source加载的自定义函数
```

```bash
mcd.sh

mcd(){
	mkdir -p "$1" && cd "$1"
}

//这是mcd文件可能的结构
//$1 表示提供的第一个参数 -p 表示即使父目录不存在也能成功创建
```

```bash
// suppose we are at dir ~/m/t/test
cd ..
rmdir test
// note that rmdir only removes a empty dir
mkdir test
cd $_
// $_ 是一个非常特殊的 Shell 变量。它的意思是 "上一个命令的最后一个参数"
// while at the same time, $? --> 获取并显示上一条执行命令的退出状态码
```

in Linux / Unix, when each command is excuted, it will return to its system a number, 这就是退出状态码, usually, 0-->success, (1-255)-->failed

e.g.

```bash
# 尝试删除一个目录
rmdir my_dir

# 检查上一条命令是否成功
if [ $? -eq 0 ]; then
  echo "目录 'my_dir' 成功删除。"
else
  echo "错误：删除目录 'my_dir' 失败！"
fi
```

