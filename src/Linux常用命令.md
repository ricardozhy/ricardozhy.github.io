---
layout: post
title: Linux常用命令
slug: linux
date: 2022-03-24 16:40
status: publish
author: 华仔仔
categories: 
  - Linux
tags: 
  - Linux
excerpt: Linux常用命令
---

Linux常用命令
欢迎交流GitHub：Ricardo-Zzhao @[https://github.com/Ricardo-Zzhao](https://github.com/Ricardo-Zzhao)

邮箱：ricardoz_y@qq.com

博客：[Ricardoz's Site](https://mblog.ricardoz.site)

# （1）指令名称：pwd

pwd命令也是最常用最基本的命令之一，用于显示用户当前所在的目录。


![](https://img-blog.csdnimg.cn/9d99f7e0ba154ae3959b49270b25f2c5.png#pic_center)

# （2）指令名称：cd 

cd命令不仅显示当前状态，还改变当前状态，它的用法跟dos下的cd命令基本一致。 
cd ..可进入上一层目录 
cd -可进入上一个进入的目录 
cd ~可进入用户的home目录
![](https://img-blog.csdnimg.cn/f2e51629b7104d0bb4d6a0cccab0e1d3.png#pic_center)

# （3）指令名称：cp  

 使用方式： 
cp [options] source dest 
cp [options] source... directory 
说明：将一个档案拷贝至另一档案，或将数个档案拷贝至另一目录。 

范例： 
将档案 aaa 复制(已存在)，并命名为 bbb : 
cp aaa bbb 
将所有的C语言程式拷贝至 Finished 子目录中 : 
cp *.c Finished
![](https://img-blog.csdnimg.cn/d1aa4842d7c14bce9a82af050c2ccac3.png#pic_center)
![](https://img-blog.csdnimg.cn/0984f607d2c7473394d8300d681cb2ad.png#pic_center)

# （4）名称：mv 

使用方式：mv [options] source dest 
mv [options] source... directory 
说明：将一个档案移至另一档案，或将数个档案移至另一目录。 
参数：-i 若目的地已有同名档案，则先询问是否覆盖旧档。 
范例： 
将档案 aaa 更名为 bbb : 
mv aaa bbb 
将所有的C语言程序移至 Finished 子目录中 : 
mv -i *.c /Finished

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/bbe43586652c438d971cc4571b6d78c7.png#pic_center)

# （5）指令名称 : chmod 

使用方式 : chmod [-cfvR] [--help] [--version] mode file... 
说明 : Linux/Unix 的档案存取权限分为三级 : 档案拥有者、群组、其他。利用 chmod 可以藉以控制档案如何被他人所存取。 

mode : 权限设定字串，格式如下 : [ugoa...][+-=][rwxX]...][,...]，其中u 表示该档案的拥有者，g 表示与该档案的拥有者属于同一个群体(group)者，o 表示其他以外的人，a 表示这三者皆是。 

+ 表示增加权限、- 表示取消权限、= 表示唯一设定权限。
  r 表示可读取，w 表示可写入，x 表示可执行，X 表示只有当该档案是个子目录或者该档案已经被设定过为可执行。

范例 :将档案 file1.txt 设为所有人皆可读取 : 
chmod ugo+r file1.txt 
将档案 file1.txt 设为所有人皆可读取 : 
chmod a+r file1.txt 
将档案 file1.txt 与 file2.txt 设为该档案拥有者，与其所属同一个群体者可写入，但其他以外的人则不可写入 : 
chmod ug+w,o-w file1.txt file2.txt 
将 ex1.py 设定为只有该档案拥有者可以执行 : 
chmod u+x ex1.py 
将目前目录下的所有档案与子目录皆设为任何人可读取 : 
chmod -R a+r * 
此外chmod也可以用数字来表示权限如 chmod 777 file 
语法为：chmod abc file 
其中a,b,c各为一个数字，分别表示User、Group、及Other的权限。
r=4，w=2，x=1 
若要rwx属性则4+2+1=7； 
若要rw-属性则4+2=6；
若要r-x属性则4+1=7。
范例： 
chmod a=rwx file        和    chmod 777 file    效果相同 
chmod ug=rwx,o=x file   和    chmod 771 file    效果相同 
若用chmod 4755 filename可使此程式具有root的权限
![](https://img-blog.csdnimg.cn/69feb178745844c994d52abed69fb58b.png#pic_center)
![](https://img-blog.csdnimg.cn/4825ca2fa75f403db774c1d47a97484e.png#pic_center)

 # （6）指令名称 : ls 

使用方式 : ls [-alrtAFR] [name...] 
说明 : 显示指定工作目录下之内容（列出目前工作目录所含之档案及子目录)。 

范例： 
列出目前工作目录下所有名称是 s 开头的档案，愈新的排愈后面 : 
ls -ltr s* 
将 /bin 目录以下所有目录及档案详细资料列出 : 
ls -lR /bin 
列出目前工作目录下所有档案及目录；目录于名称后加 "/", 可执行档于名称后加 "*" : 
ls -AF 
![](https://img-blog.csdnimg.cn/5a77d2e6dc28484b8b11ba486a732814.png#pic_center)
![](https://img-blog.csdnimg.cn/d86fe5ce452a4dc4b4a21bc273027457.png#pic_center)

 # （7）指令名称：rm 

  使用方式：rm [options] name... 
说明：删除档案及目录。 


范例：
删除所有C语言程式档；删除前逐一询问确认 : 
rm -i *.c 
将 Finished 子目录及子目录中所有档案删除 : 
rm -r Finished 
![](https://img-blog.csdnimg.cn/0bdaaaf06ef241d29d9d60d8274c14c0.png#pic_center)
![](https://img-blog.csdnimg.cn/03a5ff4b319b45db9c5e6d23b5f309ac.png#pic_center)

 # （8）指令名称：rmdir 

使用方式： rmdir [-p] dirName 
说明： 删除空的目录。 
参数： -p 是当子目录被删除后使它也成为空目录的话，则顺便一并删除。 
范例： 
将工作目录下，名为 AAA 的子目录删除 : 
rmdir AAA 
在工作目录下的 BBB 目录中，删除名为 Test 的子目录。若 Test 删除后，BBB 目录成为空目录，则 BBB 亦予删除。 
rmdir -p BBB/Test 

![](https://img-blog.csdnimg.cn/703e692640694e6892618c45923bdb68.png#pic_center)

 # （9）指令名称：touch 

  使用方式： 
touch [-acfm] 
[-r reference-file] [--file=reference-file] 
[-t MMDDhhmm[CC]YY][.ss] 
[-d time] [--date=time] [--time={atime,access,use,mtime,modify}]
[--no-create] [--help] [--version] 
file1 [file2 ...] 
说明：
touch 指令改变档案的时间记录。 ls -l 可以显示档案的时间记录。
![](https://img-blog.csdnimg.cn/ea8a4a8a30cc4ca692887eca1cdf9824.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmljYXJkb1p6eno=,size_16,color_FFFFFF,t_70,g_se,x_16#pic_center)

 # （10）指令名称：gzip 

说明：gzip命令用于压缩文件。 
参数 ： -d 将压缩文件解压
范例：
如果要将ye.txt文件压缩，可用如下命令： 
gzip ye.txt 
这样就可以压缩文件并在文件名后面加上gz扩展名，变成文件ye.txt.gz。 
解压缩文件可用gzip -d命令实现： 
gzip -d ye.txt.gz 
这样就可以解压缩文件并删除gz扩展名。


![](https://img-blog.csdnimg.cn/248a7cdddbad4bba8aff7d8d1e26a2aa.png#pic_center)

# （11）指令名称：tar

说明：tar可以为文件和目录创建档案。利用tar，用户可以为某一特定文件创建档案（备份文件），也可以在档案中改变文件，或者向档案中加入新的文件。tar最初被用来在磁带上创建档案，现在，用户可以在任何设备上创建档案，如软盘。利用tar命令，可以把一大堆的文件和目录全部打包成一个文件，这对于备份文件或将几个文件组合成为一个文件以便于网络传输是非常有用的。

范例：
可用如下方法建立tar档案： 
tar cvf 
例如，如果要将当前目录中所有文件存档到ye.tar中，可用如下命令： 
tar cvf ye.tar *.* 
要浏览档案内容，将c选项变成t。如果要浏览ye.tar档案中的内容，可用如下命令： 
tar tvf ye.tar 
要取出档案内的内容，将c选项变成x。如果要将ye.tar档案中的内容取到当前目录中，可用如下命令： 
tar xvf ye.tar

新版的tar可以直接访问和建立gzip压缩的tar档案，只要在tar命令中加上z 选项就可以了。例如： 
生成压缩档案ye.tar.gz ：
tar czvf ye.tar *.txt 
显示压缩档案ye.tar.gz的内容：
tar tzvf ye.tar *.txt 
取出压缩档案ye.tar.gz的内容：
tar xzvf ye.tar *.txt 
![](https://img-blog.csdnimg.cn/d6ce5175e26a463a8d6d27344180b1dd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmljYXJkb1p6eno=,size_16,color_FFFFFF,t_70,g_se,x_16#pic_center)
![](https://img-blog.csdnimg.cn/38d58471b7ba4614bf12125c96bf5639.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmljYXJkb1p6eno=,size_17,color_FFFFFF,t_70,g_se,x_16#pic_center)

# （12）指令名称：mail 

  使用方式：mail [-iInv] [-s subject] [-c cc-addr] [-b bcc-addr] user1 [user 2 ...] 
说明： 
mail 不仅只是一个指令， mail 还是一个电子邮件程序。

参数：
s 邮件标题 
c 邮件地址 （2个地址以上用，一个地址不用加此参数）

范例： 
①将信件送给一个或以上的电子邮件地址，由于没有加入其他的选项，使用者必须输入标题与信件的内容等。
mail user01@mcs.njnu.edu.cn
系统会提示输入“subject”
②将 mail.txt 的内容寄给yzhu@mcs.hpc.njnu.edu.cn ，同时抄送给root@mcs.hpc.njnu.edu.cn
mail -s “标题” -c yzhu@mcs.hpc.njnu.edu.cn  root@mcs.hpc.njnu.edu.cn <  mail.txt 
接收到的邮件都保存在目录 /var/spool/mail/用户名

![](https://img-blog.csdnimg.cn/4587efbbb7e74d0ba2e80bf51d7582f9.png#pic_center)
![](https://img-blog.csdnimg.cn/3185aea2a4ed4a7097113a5528dac893.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmljYXJkb1p6eno=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
![](https://img-blog.csdnimg.cn/cf4de1453333475bba8315cf53e5abcc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmljYXJkb1p6eno=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

# （13）指令名称 : wall （选做）

使用方式 :
wall [ message ] 
使用说明： 
wall 会将讯息传给每一个 mesg 设定为 yes 的上线使用者。
例子 :
传讯息"hi" 给每一个使用者 : 
wall hi
![](https://img-blog.csdnimg.cn/2733f03cd0554a308b87e8abd2ec72e5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmljYXJkb1p6eno=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

# （13）感悟

做完本次实验感觉还是有很多的收货的，原本对这些操作只是有点映像，现在对于这些操作更加的得心应手了，知道了mail和wall的用法，同时老师让我们看more，CJSON的源码，感觉对这些还是有点难度的，有点看不懂，希望在以后的学习中能过加强对这些的理解。
