# tar
Linux 系统中最常用的打包解包命令

## 打包

```
tar -cvf test.tar test/
```
- -c 将多个文件或目录进行打包
- -v 显示打包过程
- -f 指定包的文件名

## 解包

```
tar -xvf test.tar
```

- -x 解包操作
- -v 显示解包过程
- -f 指定包的文件名
- -t 只查看包中有哪些文件或目录，不做解包操作

## 打包且压缩

```
tar -zcvf test.tar.gz /test
```

- -z 压缩和解压缩 ".tar.gz" 格式
- -j 压缩和解压缩 ".tar.bz2" 格式

## 解包解压缩

```
tar -zxvf test.tar.gz
```

# zip
是一种相当简单的分别压缩每个文件的存储格式

```
zip -rv test.zip test/
```

- -r 递归压缩目录
- -v 显示详细的压缩过程
- -压缩级别 范围 1~9，-1 代表压缩速度更快 -9 代表压缩效果更好
- -u 更新压缩文件，即往压缩文件中添加新文件

# unzip
查看和解压缩 zip 文件

```
unzip test.zip
```

- -d 目录名 将压缩文件解压到指定目录下
- -n 解压时并不覆盖已经存在的文件
- -o 解压时覆盖已经存在的文件
- -v 查看压缩文件的信息，但不做解压操作
- -t 测试压缩文件有无损坏，但不解压
- x 文件列表 解压文件，但不包含文件列表中指定的文件

# gzip
只能用来压缩文件，不能压缩目录(只压缩，不打包)

```
gzip -r test/
```

# gunzip
解压 gzip 压缩过的文件

```
gunzip install.log.gz
```

# bzip2
只能压缩文件，不能压缩目录(只压缩，不打包) <br />
".bz2"格式的算法更先进、压缩比更好；而 ".gz"格式相对来讲时间更快。

# bunzip2
解压 bzip2 压缩过的文件