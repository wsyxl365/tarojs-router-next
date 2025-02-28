# tarojs-router-next

[![](https://img.shields.io/npm/v/tarojs-router-next.svg?style=flat-square)](https://www.npmjs.com/package/tarojs-router-next)
[![](https://img.shields.io/npm/l/tarojs-router-next.svg?style=flat-square)](https://www.npmjs.com/package/tarojs-router-next)
[![](https://img.shields.io/npm/dt/tarojs-router-next.svg?style=flat-square)](https://www.npmjs.com/package/tarojs-router-next)

它是一个小巧的 [Taro(小程序)](https://taro-docs.jd.com/taro/docs/README/index.html) 路由库，为你提供以下特性：

- 自动生成带参数类型提示的路由方法
- 允许传递任意类型、任意大小的参数数据
- 同步的路由方法调用
- koa体验一致的路由中间件



## 快速开始

[使用文档](http://lblblib.gitee.io/tarojs-router-next/guide/quike/start)，[API 文档](http://lblblib.gitee.io/tarojs-router-next/api/class/router)

[Demo（代码）](https://github.com/lblblong/tarojs-router-next/tree/master/examples)，[Demo（微信开发者工具打开）](https://developers.weixin.qq.com/s/2CcFkJmo7Dpb)



#### 安装核心依赖

```shell
$ npm install --save tarojs-router-next
```


#### 安装路由方法自动生成插件

```shell
$ npm install --dev tarojs-router-next-plugin
```

在 [编译配置(/config/index.js)](https://taro-docs.jd.com/taro/docs/config-detail/#plugins) 的 plugins 字段中引入插件：

```typescript
const config = {
  plugins: ['tarojs-router-next-plugin'],
}
```



## 解决什么问题

1. 路由跳转的页面 url 没有类型提示容易输错
2. 路由传参需要手动拼接参数、无法携带任意类型、任意大小的数据
3. 路由方法是异步的，页面通过 `EventCannal` 通信，事件的回调方法可读性差、耦合度高、只能在回调内部处理异常
4. 路由跳转的鉴权等实现起来比较麻烦



## 如何解决

**1. 路由跳转的页面 url 没有类型提示容易输错**

tarojs-router-next 不需要使用者手写页面 url，它会监听项目 `src/pages` 内容变化，自动为使用者生成对应的路由方法并附加到 [Router](http://lblblib.gitee.io/tarojs-router-next/api/class/router) 类上，比如以下列子：

左边的页面结构会生成右边的 [Router.to\*\*](http://lblblib.gitee.io/tarojs-router-next/api/class/router#to-options-) 系列方法，全都挂在 [Router](http://lblblib.gitee.io/tarojs-router-next/api/class/router) 类上

![](http://lblblib.gitee.io/tarojs-router-next/images/code1.png)

**2. 路由传参需要手动拼接参数、无法携带任意类型、任意大小的数据**

tarojs-router-next 允许直接传递一个对象给 `params`，它会把 `params` 展开拼接到 `url` 后面。并且还可以接收一个 `data` 参数，`data` 可以传递任意类型、任意大小的数据。

![](http://lblblib.gitee.io/tarojs-router-next/images/code2.gif)

**3. 路由方法是异步的，页面通过 `EventCannal` 通信，事件的回调方法可读性差、耦合度高、只能在回调内部处理异常**

tarojs-router-next 的路由跳转会返回一个 `Promise`，可以用 `async/await` 写出同步代码，详细参考 [同步的路由方法](http://lblblib.gitee.io/tarojs-router-next/guide/quike/sync-router)

**4. 路由跳转的鉴权等实现起来比较麻烦**

自己实现路由的鉴权是比较麻烦的事情，而 tarojs-router-next 提供非常易于理解的路由中间件功能，详细参考 [路由中间件](http://lblblib.gitee.io/tarojs-router-next/guide/quike/middleware)



## 平台与框架支持

#### 框架支持
支持所有 `Taro` 可支持的框架（`React`、`Vue`、`Vue3`、`Nerv`）

#### 小程序支持
理论上支持所有 `Taro` 可支持的小程序平台，目前已在 `微信小程序`、`QQ小程序`、`支付宝小程序` 测试通过

#### H5 支持
支持

#### React Native 支持
暂不支持