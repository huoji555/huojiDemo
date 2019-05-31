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
