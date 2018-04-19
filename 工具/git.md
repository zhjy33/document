# git
##1、解决gitignore失效问题
因为git有缓存，要想使刚配置的gitignore生效，需要清理缓存<br>
git rm -r --cached .  <br>
git add .<br>
git commit -m "update gitignore"<br>
运行上面三条命令