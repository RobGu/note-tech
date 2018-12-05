# 在 window git-bash 上用 shell 脚本提交小程序代码
1. 找到开发者工具 bin 目录
2. 新建 `cli` 文件, 内容如下
```sh
#!/bin/bash

cd "${0%/*}"

node ./cli.js $*
```
