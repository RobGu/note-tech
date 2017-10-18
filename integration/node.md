# Install

## Pre-Install
在 `~/.zshrc` 或者 `.bashrc` 下添加

```
export NVM_NODEJS_ORG_MIRROR=http://npm.taobao.org/mirrors/node
```

## MAC or Ubuntu
```
curl https://raw.githubusercontent.com/creationix/nvm/v0.33.5/install.sh | bash
. ~/.zshrc
nvm install 7.10.0
```

## Windows
直接到 https://npm.taobao.org/mirrors/node 下载 nodejs 并安装

## Post-Install
由于 国内访问 npm 源比较慢,建议使用淘宝源
```
npm config set registry https://registry.npm.taobao.org
```
