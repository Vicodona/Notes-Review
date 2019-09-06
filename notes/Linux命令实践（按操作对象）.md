## 文件

### 查看目录以及目录下的文件
```
ls -rtl                                    # 按修改时间倒叙列出所有目录和文件 ll -rt
                                           # -t,以文件修改时间排序
			                   # -r,以相反次序排序
										   
ls -lSh                                    # 按文件大小列出目录下的文件（降序）
                                           # -S,按文件大小排位
										 
ls -|*|grep "^-"| wc -|                    # 计算当前目录下的普通文件数量（-，普通文件|d，目录文件|l，链接文件等）										 

ls -l --block-size=M                       # 使用MB作为单位大小
ls -d */                                   # 只列出目录
ls -n                                      # 以数字方式列出项的所有者和所有组（即UID和GID）
ls -R                                      # 递归列出子目录

du -s * | sort -nr                         # 按文件大小列出目录下的文件（降序）
                                           # -s,当前文件夹的大小	

find /dir -mmin -30 -name "*.c"            # 查找30min中内被修改过的 .c 文件
find /dir -mtime 0 -type f                 # 查找最近一天被修改过的普通文件
						   

```

#### 文件查看

#### 查看整个文件：正向查看/反向查看
```
cat file  # 正向查看文件，一次性输出文件内容。为了控制滚屏，可以按Ctrl+S键，停止滚屏；按Ctrl+Q键可以恢复滚屏。cat可创建、合并文件。
          # -n,对文件内容编号
          # -b,与 -n 相似，但不对空白行编号
          # -s,多行空白行合并为一行空白行

tac file  # 按行反序显示文件内容  
rev file  # 反转显示文件内容
```
#### 分屏查看文件
```
more file  # 分页显示指定的文件内容
           # -num,一次性显示的行数
           # +num,从第 num 行开始显示
           # ctrl+f/空白键,向下滚动一屏
	   # ctrl+b,返回上一屏
           		   

less file  # 分页显示指定的文件内容

区别：
1、翻页：more只能向下翻页，less不仅可以向下翻页，还可以向前翻页；
2、查找字符串：more只能向下查找，less不仅可以向下查找，也可以向上查找
3、滚动：less 允许往回滚动已浏览过的内容
4、速度：因为less并未在一开始就读入整个档案，所以预览大型文件时，less比more快
```

#### 查看部分内容
```
head file  # 显示文件前 N 行内容，默认前10行内容
           # -n,显示文件的前多少行内容，默认前10行内容
           # -c,显示文件的前多少字节内容
		   

tail file  # 显示文件后 N 行内容，默认为后 10 行内容
           # -c,显示文件后多少字节
           # -n,显示文件后多少行

head -c 10m                                # 截取文件中10M 内容
tail -f file                               # 查看结尾 监视日志文件
tail -F file                               # 监视日志并重试, 针对文件被mv的情况可以持续读取
split -C 10M                               # 将文件切割大小为10M -C按行		   
```

### 编辑文件

```
mkdir dirname                              # 创建目录(-p: 目录不存在怎创建 -m:设置权限)
rmdir dirname                              # 删除空目录
touch file                                 # 创建空白文件
rm -rf dirname                             # 不提示删除非空目录(-r:递归删除 -f:强制 -i:删除前逐一询问确认)

dos2unix                                   # windows文本转linux文本
unix2dos                                   # linux文本转windows文本

enca filename                              # 查看编码  安装 yum install -y enca
md5sum                                     # 查看md5值

ln sourcefile newfile                      # 硬链接
ln -s sourcefile newfile                   # 符号连接

readlink -f /data                          # 查看连接真实目录

file                                       # 检查文件类型
umask                                      # 更改默认权限
uniq                                       # 删除重复的行
uniq -c                                    # 重复的行出现次数
uniq -u                                    # 只显示不重复行

paste a b                                  # 将两个文件合并用tab键分隔开
paste -d'+' a b                            # 将两个文件合并指定'+'符号隔开
paste -s a                                 # 将多行数据合并到一行用tab键隔开

chattr +i /etc/passwd                      # 不得任意改变文件或目录 -i去掉锁 -R递归

locate aaa                                 # 搜索
wc -l file                                 # 查看行数
cp filename{,.bak}                         # 快速备份一个文件
cp a b                                     # 拷贝不提示 既不使用别名 cp -i

rev                                        # 将行中的字符逆序排列
echo "1,2" | rev

comm                                       # 对两个有序的文件进行比较(comm [- 123] file1 file2)
                                           # 三列输出：-1:仅在file1中出现的行 -2:仅在file2中出现的行 -3:在两个文件中都存在的行
					   # 如果文件名用 “- ”，则表示从标准输入读取
										   
comm - 12                                  # 就只显示在两个文件中都存在的行
comm - 23                                  # 只显示在第一个文件中出现而未在第二个文件中出现的行
comm - 123                                 # 则什么也不显示

cksum                                      # 检查文件的CRC是否正确，确保文件从一个系统传输到另一个系统的过程中不被损坏
                                           # 输出两列：校验码，字节数
echo "10.45aa" |cksum                      # 字符串转数字编码，可做校验，也可用于文件校验

iconv -f gbk -t utf8 source.txt > new.txt  # 转换编码
                                           # -f:原始文本编码 -t: 输出编码 -o:输出文件

od                                         # 查看特殊格式文件
xxd /boot/grub/stage1                      # 16进制查看
hexdump -C /boot/grub/stage1               # 16进制查看

rename source newfile                      # 重命名 可正则
watch -d -n 1 'df; ls -FlAt /path'         # 实时某个目录下查看最新改动过的文件
cp -v  /dev/dvd  /rhel4.6.iso9660          # 制作镜像
diff suzu.c suzu2.c  > sz.patch            # 制作补丁
patch suzu.c < sz.patch                    # 安装补丁
```
