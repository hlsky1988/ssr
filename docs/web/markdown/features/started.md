# 快速开始

本篇章将介绍如何快速的在本地创建一个基于 `ssr` 框架的项目。由于我们是基于插件化的架构，所以我们能够支持任意前端框架与任意服务端框架的组合。目前官方提供了前端框架 `React`， `Vue2`， `Vue3`与服务端框架 [Midway.js](https://midwayjs.org/) [Nest.js](https://nestjs.com/) 的默认集成示例让大家迅速创建。

如果你想使用其他的服务端框架例如[daruk.js](https://github.com/darukjs/daruk) 等。那么你可以参考默认的服务端框架插件[示例](./features$plugin)来迅速的编写一个服务端插件。这是非常简单的一件事情。因为我们的服务端插件没有任何额外逻辑。


## create-ssr-app

我们提供了 [create-ssr-app](https://github.com/zhangyuang/create-ssr-app) 脚手架来让用户可以迅速的创建不同类型的应用。

目前官方提供了以下类型的模版给开发者直接使用。用户可根据自己的实际技术栈选择不同的模版进行开发。

虽然技术栈不同但开发思想是一致的，在任何技术栈的组合中我们的开发命令, 构建命令以及渲染原理都是完全一致的

注意: 如果你想使用 `Serverless` 的能力来迅速发布你的应用，那么你应该选择基于 `Midway.js` 的模版应用。关于 `Serverless` 开发更加详细的介绍可以阅读[Serverless](./features$serverless) 章节。如无特殊需求，我们建议创建 `Serverless` 类型的应用来享受一站式的开发部署能力

- [midway-react-ssr](https://github.com/ykfe/ssr/tree/dev/example/midway-react-ssr) 同时支持 Serverless 形式部署以及传统 Node.js 应用类型部署
- [midway-vue-ssr](https://github.com/ykfe/ssr/tree/dev/example/midway-vue-ssr) 同时支持 Serverless 形式部署以及传统 Node.js 应用类型部署
- [midway-vue3-ssr](https://github.com/ykfe/ssr/tree/dev/example/midway-vue3-ssr) 同时支持 Serverless 形式部署以及传统 Node.js 应用类型部署
- [nestjs-react-ssr](https://github.com/ykfe/ssr/tree/dev/example/nestjs-react-ssr) 支持 传统 Node.js 应用类型部署
- [nestjs-vue-ssr](https://github.com/ykfe/ssr/tree/dev/example/nestjs-vue-ssr) 支持 传统 Node.js 应用类型部署
- [nestjs-vue3-ssr](https://github.com/ykfe/ssr/tree/dev/example/nestjs-vue3-ssr) 支持 传统 Node.js 应用类型部署

### 命令行创建项目 

通过 `npm init` 命令我们可以创建上述的任意模版

```shell
$ npm init ssr-app my-ssr-project --template=midway-vue3-ssr # 这里可以选择上述任意模版
$ cd my-ssr-project && npm i
$ npm start # 启动服务，等价于 npx ssr start
$ open http://localhost:3000 # 访问应用
$ npm build # 资源构建，等价于 npx ssr build
$ npm run start:vite # 以 Vite 模式启动，等价于 npx ssr start --vite
```

注意: 当 `Node.js version >=15` 或者 `npm version >= 7` 时，应使用 `npm init ssr-app my-ssr-project -- --template=midway-react-ssr` 来正确的传递参数

## 应用部署

我们提供了传统 Node.js 应用部署以及 Serverless 形式部署两种方式。

当你选择了基于 `Midway.js` 的模版后，我们额外提供了 `ssr deploy` 命令来将你的应用迅速发布到阿里云或者腾讯云。需要了解详细的发布流程可以阅读[应用部署](./features$deploy)章节
### Serverless 部署

以 Serverless 形式迅速发布应用

```shell
$ npm run deploy # 应用发布, 等价于 npx ssr deploy
$ npm run deploy:tencent # 发布到腾讯云 等价于 npx ssr deploy --tencent
```

### 传统 Node.js 应用形式部署

在 `Midway.js` 场景下我们使用 [egg-scripts](https://eggjs.org/zh-cn/core/deployment.html) 进行部署

在 `Nest.js` 场景下我们使用 [pm2](https://pm2.keymetrics.io/) 进行部署

```shell
$ npm run prod 
```

## 使用其他框架部署

若开发者不想使用 `Midway.js`, 希望选择其他的框架例如 `Nest.js` 进行开发，并且希望获得 `Serverless` 的部署能力，那么可能需要手动调用不同平台提供的工具来进行部署。例如阿里云提供的 [fun](https://github.com/alibaba/funcraft?spm=a2c4g.11186623.2.8.16e15124xBSLBb) 工具来进行部署，但成本可能略高。且需要将返回的内容格式从默认的 `stream` 改成 `string`。因为云平台不支持 `stream` 格式
