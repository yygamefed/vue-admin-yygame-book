# 快速上手

以下假设web所在的maven module名为pas-web

拉取项目后，你需要做以下操作：

执行MAVEN 命令

### 安装

```text
mvn clean install
```
待maven完全安装好后执行下一步，期间如果web模块的frontend-maven-plugin抛出错误，请看常见问题


### 配置前端代理转发

**介绍**
开发过程前后端分离，分别起两个服务器进程（开两个端口）；一个是java服务器（以下称接口服务器），一个是node服务器（以下称前端服务器）。我们开发预览的时候直接访问的是前端服务器，至于接口方面，则是先配置好转发规则，由前端服务器转发请求到接口服务器。

比如,java服务器启动的的是8080端口，localhost:8080/myapp
前端服务器启动的是9090端口,localhost:9090/
加入以下配置（该配置在框架内已包含）

```js
'/api': {
    target: 'http://localhost:8080/',
    changeOrigin: true,
    onProxyRes: function (proxyRes) {
      var resCookie = proxyRes.headers['set-cookie'];
      if (resCookie != null && resCookie.length > 0) {
        var resultArr = resCookie[0].split(";");
        var resultStr = '';
        for (var i in resultArr) {
          if (resultArr[i].toLowerCase().indexOf('path=') >= 0) {
            resultStr += 'Path=/;';
          } else {
            resultStr += resultArr[i] + ';'
          }
        }
        proxyRes.headers['set-cookie'][0] = resultStr;
      }
    },
    pathRewrite: {
      // 如果是接口服务器是根目录 则直接重写到根目录"/"
      // '^/api': '/'
      // 如果接口服务器不是在根目录 则重写到目录"/xxx"
      '^/api': '/myapp'
    }
  }
```


则接口/myapp/user/list.do访问流程是这样的：
- 页面方面直接请求的是localhost:9090/api/user/list.do
- (这一步是透明的)前端服务器匹配到api/这个规则，会将请求转发到localhost:8080/myapp/user/list.do
- onProxyRes是处理返回头的函数，这里已经有相关处理，处理的内容是将返回的setcookie字段的path重置到根目录，若不符合实际需求可继续修改。
- 因此最终的效果就是 请求 localhost:9090/api/user/list.do相当于请求localhost:8080/myapp/user/list.do

**配置**

在vue.config.js配置target(主要是要转发的端口)以及pathRewrite的右半部分(取决于你的接口服务器是不是在根目录下)即可,"/api"以及"^/api"不需要修改，如果你的后台服务器是8080端口并且是部署在根目录下 则不需要改动改配置文件


### 启动前端服务器

在启动了接口服务器后，到web的maven模块目录下输入命令


```bash
mvn frontend:npm@npm-run-dev
```
即可启动前端服务器


### 开始开发

- 各个页面入口在views目录下添加
- 页面使用的组件则在components目录下添加
- common目录是一些公共的组件，不推荐改动
- 菜单部分在menu.js进行配置







### 常见问题

- maven包安装时控制台报错，排除了其他插件的因素之后，确实是frontend-maven-plugin抛出错误的，可能有以下原因
    - 权限不足，要使用管理员身份执行
    - npm包安装失败，停掉maven进程，任务管理器下关掉所有node相关进程，重新执行install


