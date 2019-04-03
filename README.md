# Mac下 Brew 更新缓慢问题解决

替换现有上游，命令一行一行输入。

    cd "$(brew --repo)"
    git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

    cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
    git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

    brew update

复原

    cd "$(brew --repo)"
    git remote set-url origin https://github.com/Homebrew/brew.git

    cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
    git remote set-url origin https://github.com/Homebrew/homebrew-core

    brew update

Today :

    brew --version

    > Homebrew 2.0.6
    > Homebrew/homebrew-core (git revision d033; last commit 2019-02-22)

AND: 

    node --version

    > v10.15.3

AND:

    psql --version

    > psql (PostgreSQL) 11.2

镜像来源： [清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/)





--------------------- 
# Mac下 npm 更新缓慢问题解决 (npm的镜像替换成淘宝)

1.得到原本的镜像地址

    npm get registry 

    > https://registry.npmjs.org/

设成淘宝的

    npm config set registry http://registry.npm.taobao.org/

    yarn config set registry http://registry.npm.taobao.org/

 

 

2.换成原来的

    npm config set registry https://registry.npmjs.org/

镜像来源：[淘宝 NPM 镜像](https://npm.taobao.org/)





--------------------- 
# react-native

    brew install node

    brew install watchman

    npm install -g react-native-cli

    react-native init AwesomeProject
