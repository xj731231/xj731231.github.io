## 搭建博客流程

*具体流程请查看我的文章《快速搭建你的专属博客》，这里相当于是我搭建时的一个框架，做完这些，博客基本就成功了，接下来就是自我发挥。*

#### 账号注册

   1. ###### GitHub 注册
    
   2. ###### 仓库建立
    
   3. ###### Disqus 注册
    
   4. ###### 域名注册
     
   5. ###### 网站统计


#### git配置 + SSH

   
#### Jekyll配置

   *这一步是用来熟悉 jekyll 搭建静态博客，方便以后在本地修改文件预览效果，提高效率。*

  
#### 博客模板下载

   
#### 博客改造

   *此处针对 HUX 的模板进行改造，其他模板流程大体相同，细节处结合自己的模板。*

   > **PART 1.**  _config.yml

   > **PART 2.**  _includes

   > **PART 3.**  _layouts

   > **PART 4.**  img（推荐本地浏览器预览效果 or 上传 GitHub 后，再行修改）

   > **PART 5.**  index.html

   > **PART 6.**  CNAME

   > **PART 7.**  about.html（推荐本地浏览器预览效果 or 上传 GitHub 后，再行修改）

   > **PART 8.**  tags.html（推荐本地浏览器预览效果 or 上传 GitHub 后，再行修改）

   > **PART 9.**  _posts           存放你写的文章，至于格式，可以上网查阅或是参照我的模板里的文章，例如：

   > **PART 10.**  google299……31.html            这是我在注册谷歌分析时下载的，它推荐我放在博客里，我不知道有什么用，也没删；你可以选择删掉它，或是替换成你自己的。

   
#### 博客上传

   *博客改造很难完全完成，你可能缺乏对应的工具，亦或是看不到效果不敢贸然修改。（如果你借助 localhost:4000 本地预览，会产生两个文件夹，.jekyll-cache 和 _site ，上传前请删除。）所以，接下来我们将博客上传至GitHub仓库，上传完成后，就细节问题再做修改。*

   > **STEP 1.**  上传
   >
   > ```ruby
   > $ git init               建立一个仓库                           
   > 
   > $ git add .             选择要添加进库的文件（用 . 表示添加该文件夹所有文件）
   > 
   > $ git commit -m 'upload'       添加进入仓库（-m 后面 ' ' 相当于解释提交的内容或是目的）
   > 
   > $ git remote add origin git@github.com:XXX/XXX.git        仓库的SSH地址
   >                      例如我的：     git@github.com:xj731231/xj731231.github.io.git
   > 
   > $ git pull origin master         多人协同开发下，远程主机分支更新和本地指定分支的合并      
   > 
   > $ git push -u origin master        push上传本地文件
   > ```
   >
   > **[ 注 1 ].**  一定要进入待上传的文件夹中
   > **[ 注 2 ].**  pull 的作用，会在 FAQ 中详述，如果初次上传，此步 聊胜于无。若需 pull 完整格式，请上网查阅。

   > **STEP 2.**  若一切成功，即可。

 
## 选用工具/网站

-  [notepad++](https://notepad-plus-plus.org/downloads/)       浏览 .txt ，.html ，.yml的工具
- [Typora](https://typora.io/)               写.md文件的工具


## 问题FAQ

- **按 F12 查看源码时出现了主动混合内容的错误？**

  初始 HTML 内容通过安全的 HTTPS 连接加载，但其他资源（例如，图像、视频、样式表、脚本）则通过不安全的 HTTP 连接加载，同时加载了 HTTP 和 HTTPS 内容以显示同一个页面，且通过 HTTPS 加载的初始请求是安全的，会产生主动混合内容。针对这种情况，选择更换HTTP加载的资源即可，至于怎么更换，具体错误具体查阅。

- **缺乏对 disqus 的有效支持，博客原本使用的是多说评论？**

  加入 disqus 插件，保证每个页面都能有效运行；如果愿意探究的话，可以试试其他的评论工具。

- **git bash中 bundle install 很卡？**

  一般有两个原因，一是 great wall fire ， 二是 gem 的 source  设置不正确。解决方法：

  ```ruby
  gem sources --remove https://rubygems.org/          移除原先的来源
  
  gem sources --a https://gems.ruby-china.com         增加新的国内的来源
  
  gem sources -l                                      查看现有的来源
  ```

  **[ 注 ].**  之后的下载会快很多，rails 可以算作是一组 gem ，可以下载，不过与本文无太大关联。

- **一开始没有选择更换来源，或是换了之后效果不明显？**

  jekyll new my-blogs 的同时，会 running bundle install ，但是太卡的情况下，我们会选择 `Ctrl + C` 将其终止，这个时候处于部分安装，部分缺失的尴尬情况，一种办法是，将博客文件夹删除，重新运行命令；另一种方法，则是 cd 到博客文件夹，敲击以下命令，补全缺失的 Gemfile.lock 。

  ```ruby
  $ bundle install
  ```

  此命令会查看 Gemfile.lock 安装指定的 gem ，以保证一致和稳定。

- **遇到 Jekyll serve 执行显示错误？**

  有时还会碰到 Jekyll serve 显示错误，可能由于未在 bundle 环境中执行脚本。

  ```ruby
  $ bundle exec jekyll serve      
  ```

  它的作用是：告知在当前 bundle 的环境中执行脚本。

- **在 .md 或者 .markdown中如何链接图片？**

  本地写文章时，图片一定有个本地链接，将这些图像上传保存到 img 下，之后将文章中的本地链接全部改为 https://github.com/用户名/仓库名/raw/master/img/xxx.ipg(png) 即可。例如：我原先的图片地址为 C:\Users\Jackie Xu\Desktop\2020-04-28-Blog\1.png  ，现在上传到了 img/2020-04-28-Blog 文件夹中，那么我的图片现在的链接就变成了 https://github.com/xj731231/xj731231.github.io/raw/master/img/2020-04-28-Blog\1.png 。

- **当远程 repo 中有文件时，采取上面的上传步骤，出现 non-fast-forward 错误 ？**

  博客建完之后，发现有的地方不满意，于是我将其下载到了电脑上，修改完成后，我采用博客上传步骤，结果居然报错了！

  网上查阅可知，non-fast-forward （非快进推送）出现在远程版本库与当前版本库内容不一致的情况下，网上推荐方法为先执行 pull ，再执行 push ，合并后推送。

  **[ 注 1 ].**  这里要注意两个问题：`git pull` 会不会覆盖本地修改 ？`git pull` 相较于 `git fetch + git merge` 有什么不同 ？遗憾的是，这块知识我一知半解，所以上述问题解释不了，有兴趣的可以去看看。

  但是，大家可以注意到，我们的上传操作中，明显已经带有了 pull 命令，说明此方法不能解决问题，这里我采用了暴力上传的方式，直接将本地二次修改的文件推送到远程 repo ，但此方法会覆盖远程，版本也会改动，所以不到万不得已，不轻易使用。

```ruby
$ git push -f origin master
```

  **[ 注  2 ].**  我远程啥也没有，所以无所谓了，当然你也可以选择将修改后的文件一个个上传替换到仓库中。（我嫌麻烦没这样做）


## 搭建之旅

​		我初期的博客，是通过《徐代龙关于个人博客搭建》完成搭建的。他的博客模板来源于 GHY 大神，这是一个很好的博客模板，带有页面自适应，点击量统计等优点。徐代龙的博文里关于流程描述很详细，但我个人觉得文章顺序存在问题，容易弄混新手。在博客成功搭建之后，我觉得这个博客的主题不太适合我，于是去网上更换。

​		目前搭建起来的博客，模板来自于 HUX 大神（在知乎上挖到的宝），在这里，建议大家找模板时，多用热度高的，多用国内的，不然会陷入很多乱七八糟的麻烦中。博客搭好之后，除了基础的信息修改外，还有些配置因为年份久远失效或是出错了。这时，我在简书上看到了 0xC00005 小姐姐的文章，惊奇地发现她也使用了 Hux 的模板（所以说海内海外，皆存知己），通过查阅她的 code ，我不仅将评论插件做好了，还成功解决了原博客的一些问题。

​		BY大佬的博文是 0xC00005 小姐姐给的传送门，内容大同小异，主要是它里面针对 disqus 来自国外加载较慢的问题，提出了 Gittalk 的评论插件，所以我把它在链接中列了出来，就是给愿意鼓捣的朋友留个途径。（我看 0xC00005 也有尝试，不过后来好像删除了，所以我不打包票）

​		博客的建立少不了前期的准备，这里要感谢B站尚硅谷的 git 教学视频，正是因为它，我才走上了博客之旅。不过对于 git 的学习，我还是建议各位在网上找详细的教程，视频更为直观易懂但效率低。至于 git 上传的相关知识，我参照了_随心的文章，每当我忘记命令时，就会打开他的文章看一看。关于站酷的蒸汽工场，说实话，我是被它里面的羊毛毡动画吸引过去的，然后发现了两张不错的场景图，用在了博客封面上，推荐大家去看看他们的作品。

​		在实际操作过程中，我遇到了诸多小问题，查阅了许多大神的博文，在这里，感谢网络上所有为新手建博客贡献力量的人。

​		**声明：若博客内容有侵犯到您的权益，请随时联系我，并提供相关证明(版权证明、侵权链接等)，我会尽快将其删除。**


## 参考文章：

**Hux 大神的博客模板： https://github.com/Huxpro/huxpro.github.io**

**0xC00005 关于 Disqus 的正确使用知识： https://www.jianshu.com/p/7e4453421b8f**

**图片素材来源于站酷的蒸汽工场： https://www.zcool.com.cn/u/13601840/timeLine#tab_anchor**

**尚硅谷git配置：https://www.bilibili.com/video/BV1pW411A7a5?from=search&seid=2339699716155106176**

**_随心 git 的上传知识：https://blog.51cto.com/hellokugo/1615715**

**不蒜子 的网站计数：http://ibruce.info/2015/04/04/busuanzi/**

**GHY 大神的博客模板（旧）：https://github.com/Gaohaoyang/gaohaoyang.github.io**

**徐代龙的搭建博客指南（旧）：https://blog.csdn.net/xudailong_blog/article/details/78762262**

**廖雪峰 git 教程：https://www.liaoxuefeng.com/wiki/896043488029600**

**BYQiu 的博客搭建指南：https://www.jianshu.com/p/e68fba58f75c**

**git bash 操作文件及文件夹命令：https://blog.csdn.net/shenziheng1/article/details/77332459**
