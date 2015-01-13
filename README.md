# grunt-spm-server

[![NPM version](https://img.shields.io/npm/v/grunt-spm-server.svg?style=flat-square)](https://npmjs.org/package/grunt-spm-server)
[![Build Status](https://img.shields.io/travis/crossjs/grunt-spm-server.svg?style=flat-square)](https://travis-ci.org/crossjs/grunt-spm-server)
[![NPM downloads](http://img.shields.io/npm/dm/grunt-spm-server.svg?style=flat-square)](https://npmjs.org/package/grunt-spm-server)
[![David](http://img.shields.io/david/crossjs/grunt-spm-server.svg?style=flat-square)](https://npmjs.org/package/grunt-spm-server)
[![David](http://img.shields.io/david/dev/crossjs/grunt-spm-server.svg?style=flat-square)](https://npmjs.org/package/grunt-spm-server)

  > A Grunt task plugin to transport `CommonJS` module to `CMD` module for `SeaJS` environment dynamically.

  > Grunt 插件：通过 Web 服务实时地将 CommonJS 模块转化成 CMD 模块，方便 SeaJS 环境中的开发调试。

## 背景

- [SPM](https://github.com/spmjs/spm) 版本从 2 升级到 3，遵循的规范从 CMD 转为 CommonJS；
- 前端开发调试过程中需要对 CommonJS 模块动态 Wrapping；
- 纯前端的解决方案 [seajs-wrap](https://github.com/seajs/seajs-wrap) 存在不少弊端。

## 用法

```bash
$ npm install --save-dev grunt-spm-server
```

```js
grunt.initConfig({
  server: {
    // 开发环境
    develop: {
      options: {
        // API mocking 文件存放目录
        api: './mock',
        // 指向上级目录
        base: '..',
        release: false
      }
    },
    // 仿真线上环境
    release: {
      options: {
        base: '..',
        release: true
      }
    }
  }
});
```

```bash
$ grunt server:develop
$ grunt server:release
```

## 参数

### src

Type: `Array | String`

config 文件模板路径，可选。

### dest

Type: `String`

config 文件存放路径，可选，默认 `'lib/config.js'`。

### options.api

Type: `String`

API mocking 文件存放目录。

### options.base

Type: `String`

Default value: `'.'`

Web 服务根目录。

### options.config

Type: `Boolean`

Default value: `true`

是否生成 config 文件。

### options.port

Type: `Number`

Default value: `8851`

Web 服务侦听端口。

### options.release

Type: `Boolean`

Default value: `true`

是否模拟线上环境，为 `true` 则不执行服务端 wrapping。

### options.rule

Type: `Function`

路径匹配函数，可选，返回 `true` 则执行服务端wrapping。
