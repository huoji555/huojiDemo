### git下拉<br>
>git init     //初始化   <br>
>git remote add origin xxx   //增加远端 <br>
>git fetch origin xxx      //将远端项目下拉到本地 <br>  
>git checkout -b dev(本地分支名称) origin/dev(远程分支名称)   //在本地创建分支dev并切换到该分支 <br>
>git pull origin dev(远程分支名称)   //拉取远端分支 <br>

### git登录
>git config --global user.name <br>
>git config --global user.email <br>

### git单文件提交
>git status     //查看git上的待提交文件状态，红色在工作区，绿色在暂存区<br>
>git add ./+刚才的文件路径  //将文件从工作区，提交到暂存区，此时，git status再次查看<br>
>git commit  //输入提交信息,vi模式退出(Esc进入命令模式，:wq保存文件并退出);<br>
>git push    //上传选择的文件<br>

### Hexo
>配置gitee网站时，因为css文件加载不出来，在url部分的root后边加了子文件名称:/blog/<br>
>这样我的github文件找不到了，在想解决办法<br>
>加了gitalk评论系统，不过要求登录github才能评论，考虑会使用`Valine`<br>
>关于首页图片加载的问题，看了访问请求，图片被拦截了，鉴于以后使用的图片较多，会把图片存储在七牛云上，明天写个专门上传图片的demo<br>
>已经解决首页标签的问题，需要自己(生成文件)[https://www.jianshu.com/p/ebbbc8edcc24]<br>
>(文章基本格式)[https://blog.csdn.net/qq_32337109/article/details/78755662]<br>
>hexo clean && hexo g && hexo d  //hexo发布指令

