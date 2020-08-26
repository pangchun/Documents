# 一、远程仓库克隆至本地

步骤如下：

1. 先在github新建一个仓库。

   新建时勾上`Initialize this repository with a README`。

2. 找到仓库地址并复制。

   `https://github.com/pangchun/Documents.git`。

3. 新建一个空目录作为本地仓库。

   在该目录下`$ Git Bash Here`。

4. 克隆远程仓库。

   $ git clone `https://github.com/pangchun/Documents.git`

5. 克隆完成后会发现该目录下多了一个`.git`的目录（默认隐藏）和一个`README.md`文件。

------

# 二、本地项目上传到Github

步骤如下：

1. 创建一个本地的版本库（其实也就是一个文件夹）。

   $ mkdir test

   $ cd test

2. 把这个文件夹变成Git可管理的仓库。

   $ git init

3. 把需要上传到GitHub的文件全部复制到这test这个目录下。

4. 把文件添加到缓存区。

   $ git add .

   > 注意：`add`和`.`之间有空格，`.`代表这个test这个文件夹下的目录全部都提交。你也可以通过`$ git add fileName`把单个文件添加到缓存区。

5. 查看下缓存区现在的状态。

   $ git status

   会有提示`changes to be committed: ...`。

6. 把文件提交到本地仓库。

   $ git commit -m "Comment"

7. 连接远程仓库（SSH加密）

   - 由于本地Git仓库和Github仓库之间的传输是通过SSH加密的，所以连接时需要设置一下。

   - 创建SSH KEY。先看一下你C盘用目录下（我的是C:\Users\Asus\.ssh）有没有.ssh目录，有的话看下里面有没有id_rsa和id_rsa.pub这两个文件，有就跳到下一步，没有就通过下面命令创建。

     ```java
      $ ssh-keygen -t rsa -C "youremail@example.com"
     ```

   -  然后一路回车。这时你就会在用户下的.ssh目录里找到id_rsa和id_rsa.pub这两个文件。
   -  登录Github,找到右上角的图标，打开点进里面的Settings，再选中里面的SSH and GPG KEYS，点击右上角的New SSH key，然后Title里面随便填，再把刚才id_rsa.pub里面的内容复制到Title下面的Key内容框里面，最后点击Add SSH key，这样就完成了SSH Key的加密。  

8. 在Github上创建一个Git仓库。

   - 可以直接点New repository来创建。
   - 注意：不要勾选`Initialize this repository with a README`。

9. 连接远程仓库（也就是连接Github）。

   $ git remote add origin `https://github.com/GitHub用户名/仓库名.git`

10. 把本地库的所有内容推送到远程仓库。

    $ git push -u origin master

    由于新建的远程仓库是空的，所以要加上-u这个参数。然后进去GitHub 的新建仓库刷新就会有已经上传的文件夹了。

11. 同步远程和本地仓库

    如果新建远程仓库不是空的，例如你勾选了 Initialize this repository with a README。那么你通过命令 `$ git push -u origin master`是会报错的，这是由于你新创建的那个仓库里面的README文件不在本地仓库目录中，这时我们可以通过以下命令先将内容合并一下：

    $ git pull --rebase origin master

    再输入 $ git push origin master。

    等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需下面这样就可以了：

    $ git push origin master。

------

# ###、使用过程遇见的问题

## 1、不能解析主机

问题描述：

```java
$ git push -u origin master
fatal: unable to access 'https://github.com/pangchun/some_small_demos.git/': Could not resolve host: github.com
```

解决办法：

- 直接修改/etc/hosts文件。

- 打开 C:\Windows\System32\drivers\etc 目录下的hosts文件。
- 在底部添加 192.30.253.112 github.com。

## 2、443连接超时

问题描述：

```java
$ git push origin master
fatal: unable to access 'https://github.com/pangchun/some_small_demos.git/': Failed to connect to github.com port 443: Timed out
```

解决办法：

- 修改hosts文件,将github.com对应的行屏蔽即可。

- 打开 C:\Windows\System32\drivers\etc 目录下的hosts文件。
- 将github.com对应行用`#号`注释。`#192.30.253.112 github.com`











































































