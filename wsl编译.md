## Linux下的编译

#### 需要安装

g++

cmake

make

##### 编译常用选项：

###### 无选项编译链接

作用：将test.c预处理、汇编、编译并链接形成可执行文件。这里未指定输出文件，默认输出为a.out。

```
#g++ test.cpp
```

`-o`:

将源文件预处理、汇编、编译并链接形成可执行文件test。-o选项用来指定输出文件的文件名。（该开关后需要紧跟输出文件名）

```
-o file_name
```

`-std`：

设置编译标准，如以c++14的标准编译

```
-std=c++14
```

`-O`：

开启优化（1~3）

```
-O2
```

###### 举例：

```
# g++ test.cpp -o test -std=c++14 -O2
```

以O2优化编译test.cpp生成可执行文件test，各开关的出现顺序无影响

##### 多文件一起编译

- 方法一：同上，在g++后增加需要编译的源文件

  ```
  # g++ test.cpp test.h -o test -std=c++14 -O2
  ```

- 方法二：分别编译各个源文件，之后对编译后输出的目标文件链接。

  ```
  #g++ -c testfun.cpp //将testfun.c编译成testfun.o
  #g++ -c test.cpp //将test.c编译成test.o
  #g++ testfun.o test.o -o test //将testfun.o和test.o链接成test
  ```

##### Cmake

使用clion编程的同学对Cmakelists一定很熟悉，在需要编译的工程文件夹下填写Cmakelists.txt（或者从clion中copy）

通过

```
# cmake Cmakelists.txt
```

获得Makefile文件，再通过

```
# make
```

获得可执行的project

若linux环境中的编译器版本过低，也可修改Cmakelists.txt中的 version参数

add_executable(projec_name  ......)需要填上所有需要编译的源文件

#### 不要直接在clion工程的文件夹下cmake，会破坏这个工程导致不能用clion编译

可以弄一个副本文件夹，每次修改后手动或写脚本复制编译