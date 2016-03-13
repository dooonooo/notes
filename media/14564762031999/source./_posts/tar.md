title: tar命令
date: 2015-08-30 15:32:25
tags: 
- tar
- tar.gz
comments:

---

### 重要的内容放前面

解压tar.gz  ```tar -xzvf nginx-1.8.0.tar.gz```

归档后gzip压缩 ```tar -zcvf /tmp/etc.tar.gz /etc```(将/etc目录下的文件归档成为/tmp/etc.tar.gz)
<!--more-->
### 详细讲解

tar命令

参数：

-c ：建立一个压缩文件的参数指令(create 的意思)； <br/>
-x ：解开一个压缩文件的参数指令！<br/>
-t ：查看 tarfile 里面的文件！<br/>
> 特别注意，在参数的下达中， c/x/t 仅能存在一个！不可同时存在！<br/>
因为不可能同时压缩与解压缩。<br/>

-z ：是否同时具有 gzip 的属性？亦即是否需要用 gzip 压缩？<br/>
-j ：是否同时具有 bzip2 的属性？亦即是否需要用 bzip2 压缩？<br/>
-v ：压缩的过程中显示文件！这个常用，不建议用在背景执行过程！<br/>
-f ：使用档名，请留意，在 f 之后要立即接档名喔！不要再加参数！<br/>
> 例如使用『 tar -zcvfP tfile sfile』就是错误的写法，要写成『 tar -zcvPf tfile sfile』才对喔！<br/>

-p ：使用原文件的原来属性（属性不会依据使用者而变）<br/>
-P ：可以使用绝对路径来压缩！<br/>
-N ：比后面接的日期(yyyy/mm/dd)还要新的才会被打包进新建的文件中！<br/>
--exclude FILE：在压缩的过程中，不要将 FILE 打包！ 

