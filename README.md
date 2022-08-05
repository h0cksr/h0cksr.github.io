## 基础安装hexo

安装hexo并开启服务

```bash
npm install hexo-cli -g
npx hexo
hexo init blog
cd blog 
npm install
hexo server
```

更新主题

```bash
cd themes
git clone -b dev https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
cd butterfly
cp _config.yml _config.butterfly.yml
npm install hexo-renderer-pug hexo-renderer-stylus --save
hexo s
```

## 可同步git的hexo

配置git

```ssh
git config --global user.name h0cksr
git config --global user.email 2640605132@qq.com
ssh-keygen -t rsa -C "2640605132@qq.com"
cat ~/.ssh/id_rsa.pub
将得到的内容添加到github的/setting/SSH keys
ssh -T git@github.com #验证身份
```

上传项目

设置配置文件_config.yml:
```
deploy:
  type: git
  #  repository: https://github.com/h0cksr/h0cksr.github.io.git
  repo: https://从Settings:Developersettings:Personalaccesstokens获取的token@github.com/h0cksr/h0cksr.github.io.git
  branch: master
```

```bash
npm install hexo-deployer-git --save
hexo clean #清除之前生成的东西
hexo generate #生成静态文章(hexo g)
hexo deploy #部署文章(hexo d)
```

更新项目

```bash
hexo clean;hexo g;hexo d
```



## 更换设备

```bash
git clone git@github.com:TyroGzl/TyroGzl.github.io.git 克隆分支

.git 文件夹外的所有文件都删掉

把之前我们写的博客源文件全部复制过来，除了.deploy_git

复制过来的源文件应该有一个.gitignore，用来忽略一些不需要的文件，如果没有的话，自己新建一个，在里面写上如下内容，表示这些类型文件不需要git：
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/

git add .
git commit –m "add branch"
git push 
```



