# export_echart_image

把echart图片导出



### 安装phantomjs

系统环境：RHEL 8 / CentOS 8

参考链接<[https://linuxconfig.org/how-to-install-phantomjs-on-redhat-8#:~:text=How%20to%20install%20phantomjs%20on%20RHEL%208%20%2F,path%2C%20we%20can%20type%20the%20command%20...%20](https://linuxconfig.org/how-to-install-phantomjs-on-redhat-8#:~:text=How to install phantomjs on RHEL 8 %2F,path%2C we can type the command ... )>

也可自行搜索安装教程

1. 检查依赖包

   ```
   $ rpm -q glibc
   glibc-2.28-18.el8.x86_64
   $ rpm -q fontconfig
   fontconfig-2.13.1-2.el8.x86_64
   ```

   

   如果缺少，需要安装，使用dnf命令：

   ```
   dnf install glibc fontconfig
   ```

2. 可以访问官方网站下载二进制包[官方下载网址](https://phantomjs.org/download.html)

   ```
   cd /opt
   ```

   使用wget下载

   ```
   wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2
   ```

3. 解压缩

   ```
   tar -xvf phantomjs-2.1.1-linux-x86_64.tar.bz2
   ```

4. 添加软链接，可以方便的在任意目录下执行命令：

   ```
   ln -s /opt/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/local/bin/phantomjs
   ```

5. 检测是否安装成功

   ```
   phantomjs --version
   2.1.1
   ```

### 尝试导出echart图片

​	命令如下

```
phantomjs echarts-convert.js -options [options] -outfile [savePath] -width [width] -height [height]
```

​		options是要生成echart的数据参数，savePath图片保存路径，width图片宽，height图片高

​	进入当前项目所在的目录执行以下命令：

```
options=$(cat test.txt)
phantomjs echarts-convert.js -options ${options} -outfile ./test.png -width 1500 -height 800
```

​	会在当前项目下生成一个test.png图片，查看没有问题说明安装调试成功(记得把生成的test.png删除)