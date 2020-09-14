# deploy-cli-service

前端一键自动化部署脚手架服务，支持开发、测试、生产多环境配置。配置好后一键即可自动完成部署。

# github

[https://github.com/fuchengwei/deploy-cli-service](https://github.com/fuchengwei/deploy-cli-service)

# npm

[https://www.npmjs.com/package/deploy-cli-service](https://www.npmjs.com/package/deploy-cli-service)

# 安装

全局安装 deploy-cli-service

```shell
npm install deploy-cli-service -g
```

查看版本，表示安装成功

```shell
deploy-cli-service -v
```

<img src="https://s1.ax1x.com/2020/09/14/wBTOGd.png" alt="wBTOGd.png" style="zoom:40%;" align='left' />

本地安装 deploy-cli-service

```shell
npm install deploy-cli-service --save-dev
```

查看版本，表示安装成功

```shell
npx deploy-cli-service -v
```

<img src="https://s1.ax1x.com/2020/09/14/wBLF00.png" alt="wBLF00.png" style="zoom:40%;" align='left' />

# 使用（以下代码都以全局安装为例）

#### 1.查看帮助

```shell
deploy-cli-service -h
```

<img src="https://s1.ax1x.com/2020/09/14/wBL0Bt.png" alt="wBL0Bt.png" style="zoom:100%;" align='left' />

#### 2.初始化配置文件（在项目目录下）

```shell
deploy-cli-service init # 或者使用简写 deploy-cli-service i
```

根据提示填写内容，会在项目根目录下生成 `deploy.config.js` 文件，初始化配置只会生成 `dev` (开发环境)、`test` (测试环境)、`prod` (生成环境) 三个配置，再有其他配置可参考模板自行配置。

<img src="https://s1.ax1x.com/2020/09/14/wBOXRg.png" alt="wBOXRg.png" style="zoom:100%;" align='left' />

#### 3.手动创建或修改配置文件

在项目根目录下手动创建 `deploy.config.js` 文件，复制以下代码按情况修改即可。

```javascript
module.exports = {
  projectName: 'vue_samples', // 项目名称
  dev: {	// 环境对象
    name: '开发环境',	// 环境名称
    script: 'npm run build',	// 打包命令
    host: '192.168.0.1',	// 服务器地址
    port: 22,	// 服务器端口号
    username: 'root',	// 服务器登录用户名
    password: '123456',	// 服务器登录密码
    distPath: 'dist',	// 本地打包生成目录
    webDir: '/usr/local/nginx/html'	// 服务器部署路径(不可为空或'/')
  },
  test: {	// 环境对象
    name: '测试环境',	// 环境名称
    script: 'npm run build:test',	// 打包命令
    host: '192.168.0.1',	// 服务器地址
    port: 22,	// 服务器端口号
    username: 'root',	// 服务器登录用户名
    password: '123456',	// 服务器登录密码
    distPath: 'dist',	// 本地打包生成目录
    webDir: '/usr/local/nginx/html'	// 服务器部署路径(不可为空或'/')
  },
  prod: {	// 环境对象
    name: '生产环境',	// 环境名称
    script: 'npm run build:prod',	// 打包命令
    host: '192.168.0.1',	// 服务器地址
    port: 22,	// 服务器端口号
    username: 'root',	// 服务器登录用户名
    password: '123456',	// 服务器登录密码
    distPath: 'dist',	// 本地打包生成目录
    webDir: '/usr/local/nginx/html'	// 服务器部署路径(不可为空或'/')
  }
}
```

#### 4.部署 （在项目目录下）

注意：命令后面需要加 `--mode` 环境对象 （如：`--mode dev`）

```shell
deploy-cli-service deploy --mode dev # 或者使用 deploy-cli-service d --mode dev
```

输入 `Y` 确认后即可开始自动部署，看见如下提示说明部署完成

<img src="https://s1.ax1x.com/2020/09/14/wBzk7R.png" alt="wBzk7R.png" style="zoom:100%;" align='left' />

#### 5.本地安装扩展

如果使用本地安装命令的话，可以在项目根目录下的 `package.json` 文件中 `scripts` 脚本中添加如下代码

<img src="https://s1.ax1x.com/2020/09/14/wBzLvD.png" alt="wBzLvD.png" style="zoom:50%;" align='left' />

然后使用下面代码也可以完成部署操作

```shell
npm run deploy:dev
```

最后谢谢大家支持，欢迎 Star😜😜😜。

