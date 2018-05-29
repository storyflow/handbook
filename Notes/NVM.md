# NVM的使用

## 安装
1. 下载链接：https://github.com/coreybutler/nvm-windows
2. 使用前最好卸载已安装到全局的 node/npm  

## 语法
1. 安装node&npm  
nvm install [version]
安装最新版 nvm install latest
2. 查看安装的node&npm  
nvm ls
3. 卸载某个版本node  
nvm uninstall [version]
4. 查看所有命令  
nvm

## 遇到的问题
1. nodejs安装成功，npm未安装成功  
重新安装nvm  
2. nvm切换nodejs的时候，要用自带的cmd切换，不要用git-bash  

## 参考资料
* [NVM-windows](https://github.com/coreybutler/nvm-windows)
* [使用 nvm 管理不同版本的 node 与 npm](http://bubkoo.com/2017/01/08/quick-tip-multiple-versions-node-nvm/)