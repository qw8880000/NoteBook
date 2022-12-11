# 如何从管道里读取数据

方法一：可以通过read来读取
```sh
read LINE
while [[ ! -z $LINE ]]
do
    read LINE
done
```

方法二：使用xargs命令
```sh
ls | xargs myscript
```

方法三：从/dev/stdin读取（上一个命令的数据好像是输出到了stdin）
```sh
 info=$(cat </dev/stdin)
```

# xargs

管道实现的是将前面的stdout作为后面的stdin，但是有些命令不接受管道的传递方式，最常见的就是ls命令。有些时候命令希望管道传递的是参数，但是直接用管道有时无法传递到命令的参数位，这时候需要xargs，xargs实现的是将管道传输过来的stdin进行处理然后传递到命令的参数位上。也就是说xargs完成了两个行为：处理管道传输过来的stdin；将处理后的传递到正确的位置上。

- [xargs原理剖析及用法详解](https://www.cnblogs.com/f-ck-need-u/p/5925923.html)
