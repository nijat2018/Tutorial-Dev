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






--------------------- 
# Windows10 Webstrom - run node js server

1. Install node-gyp -> gyp can't find Python, despite Python running when you type "python"

Solution: [issues #1268](https://github.com/nodejs/node-gyp/issues/1268)

    node-gyp (or rather, gyp) needs python 2.7, python 3.x won't work.



2. node-gyp rebuild errors Duing install better-sqlite3

    [Tutorial: windows10 npm install better-sqlite3 question](https://www.jianshu.com/p/1bed6200a443)

    1: npm install --global --production windows-build-tools

    2: npm install -g node-gyp

    3: npm install better-sqlite3

    4: 如果报python 变量的错 设置python npm变量 如果不行直接加入系统的环境变量的path （好像必须是2.7版本的）

    5： 修复v140工具集缺失错误（下载v140）

注意：环境变量设置的是python3还是python2（在同一台电脑上同时可以安装Python2和Python3，并设置python3和python2）。还有检查/noprofile配置文件

    msvs_version=2017
    python=python2.7

Solution1: [issues #170](https://github.com/JoshuaWise/better-sqlite3/issues/170)

    With better-sqlite version 5.0.0, and a project that has a number of other native libraries, I had to update my windows build box setup to the following:

    0.Install the latest node 8 or node 10. Earlier versions of node (like 10.2.x) will not compile.
    1.Right-click start, Windows PowerShell (Admin)
    2.Install both vs2015 and vs2017 libraries. Each line will take ~5-10 minutes.
        npm install --global --production --vs2015 --add-python-to-path windows-build-tools
        npm install --global --production --add-python-to-path windows-build-tools node-gyp
    3.In your project, make sure you're not fighting with old build configurations. Delete both your %USERPROFILE%/.node-gyp and your project's node_modules directories.
    4.Set up %USERPROFILE%/.npmrc correctly:
        msvs_version=2017
        python=python2.7
    (where %USERPROFILE% is your home directory).





3. errors Duing install Postgres module in Node.js

Solution1: [issues stackoverflow](https://stackoverflow.com/questions/14576240/error-installing-postgres-module-in-node-js-and-2-other-node-js-questions)

Solution2: [follow the instruction in Github for  node-pg-native](https://github.com/brianc/node-pg-native)

注意： Specify Postgres bin folder in PATH variable, then don't forget to restart cmd.exe with Administrator rights

    1.Install Visual Studio C++ (successfully built with Express 2010). Express is free.
    2.Install PostgreSQL (http://www.postgresql.org/download/windows/)
    3.Add your Postgre Installation's bin folder to the system path (i.e. C:\Program Files\PostgreSQL\9.3\bin).
    4.Make sure that both libpq.dll and pg_config.exe are in that folder.