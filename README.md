##Description##
###Dol框架概述
	
##How to install DOL##
### 安装VMware并安装虚拟机Ubuntu
- [VMware教程](http://jingyan.baidu.com/article/0320e2c1ef9f6c1b87507bf6.html)
- [Ubuntu下载](http://www.ubuntu.com/download/desktop)
###为虚拟机配置环境
	$	sudo apt-get update
	$	sudo apt-get install ant
	$ 	sudo apt-get install openjdk-7-jdk
	$	sudo apt-get install unzip
###下载文件
	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz

	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
###解压文件
	新建dol的文件夹 
	$	mkdir dol
	将dolethz.zip解压到 dol文件夹中
	$	unzip dol_ethz.zip -d dol
	解压systemc
	$	tar -zxvf systemc-2.3.1.tgz
###编译systemc
	解压后进入systemc-2.3.1的目录下
	$	cd systemc-2.3.1
	新建一个临时文件夹objdir
	$	mkdir objdir
	进入该文件夹objdir
	$	cd objdir
	运行configure(能根据系统的环境设置一下参数，用于编译)
	$	../configure CXX=g++ --disable-async-updates
	编译
	$	sudo make install
	记录当前的工作路径(会输出当前所在路径，记下来，待会有用)
	$	pwd
###修改build_zip.xml
	进入刚刚dol的文件夹
	$	cd ../dol
	修改build_zip.xml文件
	找到下面这段话，就是说上面编译的systemc位置在哪里，
	<property name="systemc.inc" value="YYY/include"/>
	<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
	把YYY改成上页pwd的结果（注意，对于64位系统的机器，lib-linux要改成lib-linux64）
###编译DOL
	$	ant -f build_zip.xml all
	若成功会显示build successful
###测试
	接着可以试试运行第一个例子
	进入build/bin/mian路径下
	$	cd build/bin/main
	然后运行第一个例子
	$	ant -f runexample.xml -Dnumber=1
##Experimental exprience##
   此次实验较为简单，基本上就是配置环境，而且VMware和Ubuntu在之前就安装过，进一步减轻了这次实验的任务。此次实验中收获较大的是初步学会了用markdown进行编辑文档，就我目前所学会的Markdown语法来看，还是比较简单的，而且编辑之后显示的界面较为简洁，比Word文档的编辑效果要好很多。# ES2016_14353171
