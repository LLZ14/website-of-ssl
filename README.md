# website-of-ssl
##  1，准备环境

### a.一台虚拟主机（国内的需要备案）

我这里用的是领创云服务里的虚拟主机，而且还是最便宜的那一个（0.01￥+0.5￥认证）

[https://www.lcyidc.com](https://www.lcyidc.com/)

注册登录实名验证购买一个月

而我搞的是两台哦，一台是普通的（2￥），一台是免费的（bushi,0.01￥）

主要是我搞的东西太过于乱七八糟，而且免费主机只能绑定一个域名，而普通主机可以绑定两个域名，所以我索性就再买了一台，懒得删除配置了

购买成功如下图：

<img src=".\images\0.png" style="zoom:50%;" />

<img src=".\images\1.png" style="zoom:50%;" />





### b.一个域名

​    找有域名的小伙伴帮自己创建个二级域名；

​	友情提供一个llzai.fun**(已备案)**，可以在前面加入前缀即可，记得跟我联系添加记录，另外www.llzai.fun，我已经使用，**（mail,ftp,stp）保留使用，不开放**；

​    可以在网上查找免费的二级域名；

​    自己去注册一个阿里云上可注册，域名需要备案；（最稳定，域名注册一年，学生可以用来学习学习）

​    阿里云新用户还可以白嫖云服务器一个月，一般都采用LAMP或者LNMP来搭建，这两种我都试过，不过本文采用最简单的虚拟主机，便不再展开说了；

### c.一份网页源码

​    自己准备一份项目源码，打包成zip,方便后续上传到虚拟主机；

​    一般项目代码都是自己在调试完成后，再上传；

## 2，上传代码到云虚拟主机

点击产品服务-->虚拟主机-->操作-->登录面板



 出现提示，点击仍然发送

进入到控制台，接着点击在线文件管理，点击/wwwroot，进到该文件夹下，开始上传项目代码zip包，点击解压；

之所以把项目放在/wwwroot下，是因为一会配置域名是默认的文件夹就是这个，可以偷懒；你也可以自己自定义路径

![](.\images\2.png)





![](.\images\3.png)

##  3，绑定域名

![](.\images\4.png)

 之后便可以点击域名开始访问自己的网页了

不过要注意，这时候呢，你浏览器访问的时候，会出现不安全链接，所以我们加上ssl认证后，他就不会提示警告了，下面我们来获取免费的ssl证书

## 4，ssl认证

首先去到来此加密这个网站注册登录，这里申请的证书一开始有效期是3个月

这是链接：https://letsencrypt.osfipin.com/user-0408/user/register

 邀请码获取积分：ND8Y17QD，出自：[(1条消息) 通过Python脚本下载【来此加密的免费HTTPS SSL证书】并自动更新到服务器和阿里云CDN_异想之旅的博客-CSDN博客_来此加密](https://blog.csdn.net/weixin_44495599/article/details/122550727?ops_request_misc=&request_id=&biz_id=102&utm_term=来此加密推荐&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~sobaiduweb~default-1-122550727.blog_rank_default&spm=1018.2226.3001.4450)

上面这个邀请码不是我的，不过拿去用，可以获得5积分

接下来就是申请证书了



<img src=".\images\6.png" alt="image-20221226144445006" style="zoom:50%;" />

![](.\images\8.png)

 非vip会员只能申请两次，把握好

<img src=".\images\9.png" style="zoom:75%;" />

 之后会出现验证页面，有dns跟http验证



那个http验证我还没成功过，我用的是dns验证的

http那个我之前在nginx上部署后，是直接用阿里云的免费证书，所以也没有弄

<img src=".\images\101.png" style="zoom:75%;" />

最后证书申请成功后，下载到电脑上，解压出来

<img src=".\images\10.png" style="zoom:75%;" />

去到虚拟主机控制台-->FTP/文件管理-->ssl证书



ssl证书内容：填的是fullchain.crt这个文件里的内容，用记事本打开，复制粘贴

ssl证书密钥内容：填的是private.pem这个文件里的内容，用记事本打开，复制粘贴

<img src=".\images\11.png" style="zoom: 80%;" />

 点击保存，ssl证书状态成功

记得把下面http跳转https勾选上，保存

<img src=".\images\13.png" style="zoom:75%;" />

 重新访问域名，不会出现安全警告

<img src=".\images\12.png" style="zoom:75%;" />
