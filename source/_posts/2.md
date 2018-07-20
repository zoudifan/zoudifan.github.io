
---
title: 给自己的github仓库配置ssh key
date: 2018-04-07 00:23:31
tags: [github,SSH key,hexo配置]
categories: [github配置]
#description: github上设置SSH传输通道   #你對本頁的描述 可以省略
---
SSH通道具有良好的加密型，是能有效防止被劫持。因此在自己的github上设置SSH通道是非常有必要的。


<!-- more -->
## 1，准备工作
首先你的有一个github账号，作为程序猿我默认你是有的；其次你的电脑上面需要安装git，此工具我也默认你电脑上面是有的。
## 2，配置你本地机的SSH key 
- 打开git bash，输入如下命令`ls -al ~/.ssh`此时界面上应该有你之前添加过的SHH key，如果界面什么都没有说明你没添加过SSH key，如果存在SSH key，全部删除就行了，因为我们需要新建一个SSH key。
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE1.JPG)
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE2.JPG)
- 在git bash里面输入` ssh-keygen -t rsa -C "你的github账号"`命令，引号填写你自己的github账号。
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE3.JPG)
`Generating public/private rsa key pair.`
`Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):`直接回车
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE4.JPG)
`Enter passphrase (empty for no passphrase):`设定一个密码，也可以不设定直接回车
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE5.JPG)
`Enter same passphrase again:`在此输入密码，然后回车
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE6.JPG)
==***注意：此处你的github如果用于部署hexo博客系统的话，请不要设置密码，因为hexo自动部署如果遇到密码的话会导致部署失败。***==
- 在git bash里面输入`ssh-agent -s`
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE7.JPG)
- 在git bash里面输入`ssh-add ~/.ssh/id_rsa`
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE9.JPG)
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE10.JPG)
==***注意：这一步如果出现错误，就先输入` eval 'ssh-agent -s' `再输入`ssh-add`就可以了。***==
- 将自己的SSH  key复制到github里面去，先在git bash里面输入`clip < ~/.ssh/id_rsa.pub`就将SSH key复制到剪切板上面了。
## 3，下面就登陆你的github，将SSH key粘贴到里面去。
- 进入github的设置
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE11.JPG)
- 选择`SSH and GPG keys`选项
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE12.JPG)
- 选择`New SSH key`按钮
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE13.JPG)
- `Title`里面随便填，自己取名字就行了
- `key`里面粘贴自己刚才复制下来的本地SSH key
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE14.JPG)
即可完成SSH key的添加。
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE15.JPG)
##4，测试SSH key是否添加成功
- 在git bash里面输入`ssh -T git@github.com`，如果出现如下提示，说明你已经安装成功了，SSH key可以正常连接了。
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE16.JPG)
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE18.JPG)
## 5，大功告成
![](http://ox7cbl2vn.bkt.clouddn.com/%E5%9B%BE19.JPG)

