Shell对文件描述符的操作

### 输出

usage      | description | 
:-         | :-          | 
n>filename | 以输出的方式打开文件filename，并绑定到文件描述符n。n可以不写，默认为1。 |
n>&m       | 用文件描述符 m 修改文件描述符 n，结果就是m和n代表同一文件。n可以不写，默认为1。| 
n>&-       | 关闭文件描述符 n 及其代表的文件，n可以不写，默认为1。 |
&>filename | 将正确输出结果和错误信息全部重定向到filename。|

#### 输入

usage      | description |
:-         | :-          |
n<filename | 以输入的方式文件filename，并绑定到文件描述符n。n可以不写，默认为0。 |