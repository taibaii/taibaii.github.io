10进制转化为16进制/二进制，十六进制，base64转换为 十进制也相同方法
echo "obase=进制;值"|bc

ps -eo pid,tty,user,comm,lstart,etime | grep 24019
jstat　-gcutil 24019
jstat -class/-compiler/-gccapacity/-gcnew/-gcnewcapacity/-gcold/-gcoldcapacity/-gcmetacapacity/-gcprintcompilation

jstack -l 24019

查看CPU使用率
top -p PID -H

jmap -dump:live,file=b.map 22467 将live进程生成java堆转储快照

使用 jmap -heap PID 生成java堆的详细信息

使用 jmap -histo PID 生成java堆中对象的相关信息，包含数量以及占用的空间大小

　jstat工具特别强大，有众多的可选项，详细查看堆内各个部分的使用量，以及加载类的数量。使用时，需加上查看进程的进程id，和所选参数。以下详细介绍各个参数的意义。

　　jstat -class pid:显示加载class的数量，及所占空间等信息。

　　jstat -compiler pid:显示VM实时编译的数量等信息。

　　jstat -gc pid:可以显示gc的信息，查看gc的次数，及时间。其中最后五项，分别是young gc的次数，young gc的时间，full gc的次数，full gc的时间，gc的总时间。

　　jstat -gccapacity:可以显示，VM内存中三代(young,old,perm)对象的使用和占用大小，如：PGCMN显示的是最小perm的内存使用量，PGCMX显示的是perm的内存最大使用量，PGC是当前新生成的perm内存占用量，PC是但前perm内存占用量。其他的可以根据这个类推， OC是old内纯的占用量。

　　jstat -gcnew pid:new对象的信息。

　　jstat -gcnewcapacity pid:new对象的信息及其占用量。

　　jstat -gcold pid:old对象的信息。

　　jstat -gcoldcapacity pid:old对象的信息及其占用量。

　　jstat -gcpermcapacity pid: perm对象的信息及其占用量。

　　jstat -util pid:统计gc信息统计。

　　jstat -printcompilation pid:当前VM执行的信息。

　　除了以上一个参数外，还可以同时加上 两个数字，如：jstat -printcompilation 3024 250 6是每250毫秒打印一次，一共打印6次，还可以加上-h3每三行显示一下标题。

