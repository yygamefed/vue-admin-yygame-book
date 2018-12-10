# vue-admin后台管理框架使用文档

## 介绍

文档地址：[线上地址](https://yygame.gitbook.io/vue-admin-yygame/)

该后台管理框架UI层使用iview+adminlte+bootstrap，结合基于业务封装一些组件。开发部署方面使用vue-cli以及maven里的frontend-maven-plugin免去后端手工安装node的成本

## 环境要求

maven

## 开发工具

* 如果你使用idea，安装vuejs plugin即可
* 如果你使用eclipse开发，建议安装vscode并安装一系列推荐插件以及iview-snipperts,vuetur,vue vscode snippets
* 开发体验涉及的工具：vue调试插件

## MAVEN 命令

### 初始化安装node以及依赖包

这一步其实执行的是安装maven依赖，随意只需要顺利安装好maven依赖即可
```text
mvn --projects module名 clean install
```

### 启动前端调试服务器

```bash
cd 目录名
mvn frontend:npm@npm-run-dev
```

### 打包输出文件

```bash
cd 目录名
mvn frontend:npm@npm-run-build
```

## 开发

### 构建前端代码

开发时，在每次服务器启动前，构建一次前端代码。可加入到服务器启动配置里：

配置路径： 前端文件所在的module项目  
配置命令： frontend:npm@npm-run-build

#### 实时编译前端代码

开发时，启动后端服务器后，[启动前端调试服务器](#启动前端调试服务器),页面要按照vue.config.js所配置的端口（如后端配置8080，前端配置9090，访问页面应该是9090端口）来访问，  
前端在开发环境下访问接口，会做相关代理转发的处理解决开发过程带来的跨域问题，因此需要在proxy.config.js做相关的配置

### 组件及目录

项目基于iview3以及adminlte两套UI库封装，这两套框架内的所有组件在该项目都可以直接使用，  
另外根据业务对组件进行二次封装，框架二次封装的组件在common文件夹内，业务组件依然在components内开发

## 前端项目配置

### vue.config.js配置

### 页面菜单路由配置

### 开发体验

* 使用[实时编译前端代码](#实时编译前端代码)方式开发；

* 安装浏览器vue调试插件--[vue-devtools](https://github.com/vuejs/vue-devtools)  
         在Installation除选择对应的功能安装，electron app就是桌面端调试工具，不依赖某个浏览器，但使用时需要在本地html加入一段script脚本来连上调试器；

* vue-cli-ui [图形化界面配置项目](https://cli.vuejs.org/zh/guide/creating-a-project.html#使用图形化界面)  
        vue-cli-ui 是vue官方提供的图形化创建和管理vue项目界面，配置和管理简直不能再方便，但需要安装node来启动。  
  ![](http://img.game.dwstatic.com/f2e/static/f2egame-admin/20180723/public/readme/shot-vue-cli.png)

## 构建发布

在升龙上部署的时候需要skipTest防止执行npm-run-dev

