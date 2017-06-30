# Uniyt3D-SVN本地服务器的搭建和使用

## SVN本地服务器的搭建

### 为什么要使用SVN?
程序员在编写程序的过程中，每个程序员都会生成很多不同的版本，这就需要程序员有效的管理代码，在需要的时候可以迅速，准确取出相应的版本。可以共享SVN的内容

### Subversion是什么？
它是一个自由/开源的版本控制系统，一组文件存放在中心版本库，记录每一次文件和目录的修改，Subversion允许把数据恢复到早期版本，或是检查数据修改的历史，Subversion可以通过网络访问它的版本库，从而使用户在不同的电脑上进行操作。

### 安装SVN服务器

```c#
推荐安装VisualSVN Server.下面是Windows下免费的SVN Server端。
下载地址：http://www.visualsvn.com/server/download/
一般都会让VisualSVN server 服务端和 TortoiseSVN客户端搭配使用.
```
下载完成后双击安装，如下图：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image1.png)

点击【Next】下一步：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image2.png)

继续【Next】下一步，如下：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image3.png)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image4.png)

选择Standard Edition,继续点击【Next】下一步：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image5.png)

* Location是指VisualSVN Server的安装目录.  (一般安装在和版本库一样的硬盘里)
* Repositorys是指定你的版本库目录.
* Server Port指定一个端口.
* Use secure connection勾山表示使用安全连接.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image6.png)

点击Install,进入下一步,如下图:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image7.png)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image8.png)

勾选上Start VisualSVN Server Manager,点击Finish完成.


### 操作SVN服务器

启动VisualSVN Server Manager 如图：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image9.png)

可以在窗口的右边看到版本库的一些信息,比如状态,日志,用户认证,版本库等.

要建立版本库,需要右键单击左边窗口的Repositores,如下图:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image10.png)

#### 1.创建基本存储库

在弹出的右键菜单中选择Create New Repository或者新建->Repository:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image11.png)

选择存储库类型,勾选Regular FSFS repository(常规fsf库)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image12.png)

点击下一步：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image13.png)

选择初始库结构,勾选Empty repository,点击下一步：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image14.png)

权限设置，选择All Subversion users have Read/Write access，所有人都能访问点击Create

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image15.png)

点击Finish,创建存储库.这里是存储库的基本信息

#### 2.创建用户和组，并且需要分配权限

在VisualSVN Server Manager窗口的左侧右键单击用户组,选择Create User或者新建->User,如图:(创建用户）

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image16.png)

点击User后，进入如下图：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image17.png)

填写Username和password后，点击ok按钮后,完成创建用户

选择Groups右键，如下：（创建组）

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image18.png)

点击Create New Group,如下：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image19.png)

点击上面的【Add】按钮后添加名字，如下图

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image20.png)

在弹出窗口中填写Group name为Stundents,然后点Add按钮,在弹出的窗口中选择Stundents,加入到这个组,然后点Ok.

接下来我们需要给用户组设置权限，在MyRepository上单击右键,选择属性,如图:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image21.png)

在弹出的对话框中,选择Security选项卡,点击Add按钮,选中Students,然后添加进来,权限设置为Read/Write,如下图:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E6%9C%AC%E5%9C%B0%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA/images/image22.png)

点击确定按钮即可完成设置


## SVN的使用

### 目录的检出

#### 1、新建工作目录文件夹，目录和文件夹名称最好都用英文，在空白处按下鼠标右击  (最好在C盘之外的硬盘创建一个文件夹内进行检出)

在弹出的菜单中选择“SVN Checkout…”；

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212142115.jpg)

#### 2、在弹出的对话框中输入给的服务器地址，点击“OK”开始检出；

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212142240.jpg)

上图中的服务器网址是版本库的网址

#### 3.在进行检出前需要进行身份验证，在弹出的窗口中，显示第一项(接受永久证书):

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212142345.jpg)

#### 4.输入账号和密码,并选中左下角的Save authentication来保存授权，以后就不用每次操作都输入账号和密码.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212142605.jpg)

#### 5.点击OK后，便会从服务器上下载项目的文件到本地电脑上，效果如下：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212142807.jpg)

### 目录的更新(Update)

1、通常在你对工作目录进行修改前，为保证你的文件是最新的，需要进行更新操作；
2、在工作目录空白处点击鼠标右键，选择“SVN Update”；

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212143147.jpg)

3、会弹出对话框开始更新，并显示更新了哪些内容，库版本是多少；

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212143240.jpg)

### 文件的提交(Commit)

1、修改过的文件，会在本地显示为红色的叹号，这样的文件说明和服务器上的文件不相同，我们需要将本地修改的文件上传到服务器上。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212143910.jpg)

2、在工作目录空白处点击鼠标右键，选择“SVN Commit”；
会弹出对话框，可以输入备注信息,用于记录这次Commit操作做了什么修改，显示将要提交哪些文件，点击“OK”开始提交；

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212144008.jpg)

3、弹出对话框显示提交进度，完成后点击“OK”完成提交。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212144146.jpg)

### 文件删除(Delete)

删除文件，直接将要删除的文件删除掉，进行Commit操作即可。

### 恢复到指定版本(Update to Revision)

1.在工作目录空白处右击，选择[TortoiseSVN]->[Update to Revision]

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212144458.jpg)

2.在弹出的对话框中，点击 [Show Log]按钮

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212144612.jpg)

3.从弹出的Log Message窗体中选择要恢复到哪个版本,最后点击OK回到上一次的窗体

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212144803.jpg)

4.在上一次的窗体中已经指定的版本号.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212144914.jpg)

5.点击 OK按钮，进行版本恢复.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/SVN%E6%93%8D%E4%BD%9C/SVN%E7%9A%84%E4%BD%BF%E7%94%A8/images/20161212145051.jpg)



