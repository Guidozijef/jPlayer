# jessibuca-vue-demo

# run dist

```shell
npm run build
npm run preview
```

open browser href `http://localhost:8888/index.html`

# 重要说明

这个项目只是 jessibuca-pro-vue-demo 的 demo 项目，但是内涵 public 文件夹里面 hz-player，hz-player 是基于 jessibucaPro 改造的，所以 hz-player 的文档和 api 可完全参考 jessibucaPro，jessibucaPro 的文档地址链接：http://jessibuca.monibuca.com/pro-ai.html

# Disc

本播放器基于 jessibucaPro 做了部分优化改造，文档和 api 可完全参考 jessibucaPro；

# Docs

jessibucaPro 文档地址链接：http://jessibuca.monibuca.com/pro-ai.html

# Installation

## Yarn

yarn add hz-player

## NPM

npm install hz-player --save

# Usage

将 node_modules/hz-player 路径下的 hzPlayer 目录放置到项目根目录下，例如 public 目录下

```javascript
import HZPlayer from "hz-player";

new HZPlayer(options);
```
