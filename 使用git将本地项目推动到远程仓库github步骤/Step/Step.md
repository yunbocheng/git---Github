# 使用git将本地项目推送到远程仓库Github

### 准备工作

安装好git软件

注册好Github账号

## 使用方法

**1. 首先创建一个本地的版本库(即创建一个文件夹)**

你可以直接右键点击新建文件夹，也可以打开<font color =  "red">git-bash.exe</font>命令窗口通过命令来创建。

现在我通过命令行新建一个test文件夹(你也可以在其他的任何地方创建这个文件夹 注意：在哪个文件夹中打开<font color =  "red">git-bash.exe</font>命令，就在该文件夹下创建一个新的版本库)，并且进入该文件夹下。

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626180937.png)

**2. 进入刚才创建的版本库test （使用 <font color = "red">cd +文件夹名称</font>命令进入指定的文件夹）**

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626181136.png)

**3. 查看当前在哪个版本库中，即查看当前在哪个路径之下(绝对路径)，确定是否在 test 版本库中。(使用<font color = "red">pwd</font>命令进行查看)**

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626181509.png)

**4.  通过命令 <font style = "color :#FF0000;backgroung-color:#CCCCFF; ">git init</font> 把这个版本库变成Git可管理的仓库。**

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626181730.png)

注意 ：

**在路径的最后边出现了带括号的<font color = "red">master (master)</font>说明此时将test的这个版本库提交到了git的主分支master上.**

**这时你会发现在test里面多了个 <font  color="red">.git文件夹</font>，他是Git用来追踪和管理版本库的。**



如果你看不到，是因为它默认时隐藏文件，那你就需要设置一下让隐藏文件可见。

这时候你就可以把你的项目粘贴到这个本地Git仓库里面（粘贴之后你可以通过 <font color = "red"> git status .</font> 来查看你当前的状态）

此时还没有将文件添加到暂存区中，所有会显示 <font color = "red">nothing to commit</font> ,代表没有任何的文件。

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626190304.png)

**5. 使用命令 <font color = "red">git add .</font> 把项目添加暂存区里面去，不要忘记后面的小数点”.“，意为添加该文件夹下的所有文件**

第一种 ：<font color = "red">git add .</font>  : 代表将该文件夹下的所有文件都添加到暂存区里面。

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626192210.png)

第二种 ：<font color = "red">git add 文件名称</font> : 代表将指定的文件添加到暂存区里面。

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626192100.png)

**注意 ：绿色的代表添加到该版本库中成功  红色的代表没有添加到该版本库中** 

在这个过程中你其实可以一直使用status来查看你当前的状态。

**6.  用  <font color = "red">git commit -m "第一次提交"</font>  把项目提交到仓库。 **

-m 后面的双引号里面是本次提交的注释内容，这个可以不写，但是最好写上，不然会报错。到此，我们本地Git仓库这边的工作做完了，下面连接远程仓库（也就是连接Github）

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626195103.png)

 create mode 100644 ：代表创建模式 100644

100代表regular file（常规文件），644代表文件权限

**7. 远程仓库设置**

由于本地Git仓库和Github仓库之间的传输是通过SSH加密的，所以连接时需要设置一下：

​	7.1 	创建SSH

- 已有ssh密钥：先看一下你的C盘用户目录下有没有.ssh目录，有的话看下里面有没有  <font color = "red">id_rsa</font>  和  <font color = "red">id_rsa.pub</font>  这两个文件，有的跳到下一步。

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626200855.png)

<font color = "red">cd ~/.ssh</font> ：此命令是查看是否配置过密钥 （如果不报错说明配置过，如果报错说明没有配置过） 

<font color = "red">ls</font> : 此命令是查看配置过密钥的列表

<font color = "red">id_rsa.pub</font> : 这个是公钥文件

- 创建新的ssh密钥

  - 第一种方式：

    1.输入命令：cd ~

    2.然后输入：ssh-keygen.exe

    <img src="C:/Users/YunboCheng/AppData/Roaming/Typora/typora-user-images/image-20210626202123336.png" alt="image-20210626202123336" style="zoom:50%;" />

  - 第二种方式 ：

    首先输入<font color = "red">ssh-keygen -t rsa -C "邮箱名称"</font> 这个命令，然后一路回车。这时你就会在用户下的.ssh目录里找到id_rsa和id_rsa.pub这两个文件。

    

    7.2 	登录Github —>点击右上角的图标 —>选择Settings —>点击左边的SSH and GPG KEYS —>点击右上角的New SSH key —>Title随便填 —>把刚才id_rsa.pub里面的内容复制到Title下面的Key内容框里面 —>最后点击Add SSH key —>完成SSH Key的加密。具体步骤如下：

    <img src="C:/Users/YunboCheng/AppData/Roaming/Typora/typora-user-images/image-20210626202859880.png" alt="image-20210626202859880" style="zoom:50%;" />

    7.2	在Github上创建一个Git仓库。

    <img src="https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626203013.png" style="zoom:50%;" />



**8. 在Github上创建好Git仓库后通过命令<font color = "red">git remote add origin 想要传输到的Github仓库的SSH</font>和本地仓库进行关联**

<img src="https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626212509.png" style="zoom:50%;" />

此时这里的输入的命令是 ：<font color = "red">git remote add origin git@github.com:YunboCheng4379/test.git</font>

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626213210.png)

**注意 ：不出现任何的错误信息表示连接成功过**

**注意 :  origin 后面加的是你Github上创建好的仓库的地址。**

![](https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626212746.png)

**9. 关联好之后通过命令<font color = "red">git push -u origin master</font>将本地库的所有内容推送到远程仓（Github）**

<img src="https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626213325.png" style="zoom:80%;" />

由于新建的远程仓库是空的，所以要加上-u这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需 <font color = "red">git push origin master</font>

刷新Github页面进入刚才新建的仓库里面就会发现项目已经上传成功

<img src="https://gitee.com/YunboCheng/imageBad/raw/master/image/20210626213442.png" style="zoom:50%;" />



至此完成将本地项目上传到Github的整个过程。

注意有坑： 在上面第5步新建远程仓库的时候如果你勾选了<font color = "red">Initialize this repository with a README</font>（就是创建仓库的时候自动给你创建一个README文件），那么到了第7步你将本地仓库内容推送到远程仓库的时候就会报一个 failed to push some refs to https://github.com/guyibang/TEST2.git 的错。

原因： 由于你新创建的那个仓库里面的README文件不在本地仓库目录中，这时我们可以通过 <font color = "red">git pull --rebase origin master</font> 命令先将内容合并,此时再push就能成功了。

**总结：本地项目通过git上传到github**

1)、在本地创建一个版本库（即文件夹），通过 <font color = "red">git init</font> 把它变成Git仓库；
2)、把项目复制到这个文件夹里面，再通过 <font color = "red">git add .</font> 把项目添加到仓库；
3)、再通过  <font color = "red">git commit -m "注释内容"</font> 把项目提交到仓库；
4)、在Github上设置好SSH密钥后，新建一个远程仓库，通过  <font color = "red">git remote add origin 想要传输到的Github仓库的SSH</font>  远程仓库地址将本地仓库和远程仓库进行关联；
5)、最后通过  <font color = "red">git push -u origin master</font>  把本地仓库的项目推送到远程仓库（也就是Github）上。

------

看完的大佬们可以关注一下小编，会一直更新小技巧，免费分享给大家呦！！！

主页还有小编的微信公众号（扫码关注哟），里边也有小编分享的许多的小知识和有趣的小项目呦，欢迎大家打扰小编！！！







