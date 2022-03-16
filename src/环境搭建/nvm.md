# nvm

## mac、linux安装失败、下载慢

```bash
git clone https://github.com/nvm-sh/nvm.git
cd nvm
./install.sh

vi ~/.bash_profile

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

source ~/.bash_profile
```



## nvm install慢

```bash
# 设置淘宝源
echo 'export NVM_NODEJS_ORG_MIRROR=https://npmmirror.com/mirrors/node/' >> ~/.bash_profile
```

