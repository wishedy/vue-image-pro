# vue-image-pro

<!-- [![Build Status](https://www.travis-ci.org/dream2023/vue-image-pro.svg?branch=master)](https://www.travis-ci.org/dream2023/vue-image-pro) -->

[![license](https://img.shields.io/npm/l/vue-image-pro.svg)](https://dream2023.github.io/vue-image-pro/)
[![npm](https://img.shields.io/npm/v/vue-image-pro.svg)](https://www.npmjs.com/package/vue-image-pro)
[![size](https://img.shields.io/bundlephobia/minzip/vue-image-pro.svg)](https://www.npmjs.com/package/vue-image-pro)
[![download](https://img.shields.io/npm/dw/vue-image-pro.svg)](https://npmcharts.com/compare/vue-image-pro?minimal=true)

<!-- [![codecov](https://codecov.io/gh/dream2023/vue-image-pro/branch/master/graph/badge.svg)](https://codecov.io/gh/dream2023/vue-image-pro) -->

## English Document

[English Document](./README-EN.md)

## 介绍

组件的灵感来源于[小程序的 image 组件](https://developers.weixin.qq.com/miniprogram/dev/component/image.html) 和 [vue-avatar](https://github.com/eliep/vue-avatar) 组件, 相当于同时拥有两者的特性, 实现了包括图片自适应、响应式、当无图片时显示文字等。

## 应用场景

典型的应用场景就是头像, 当有图片是显示图片, 当无图片时显示用户名

## 相对于 vue-avatar 的改进

- 对中文友好
- 当图片宽高不一致时, 依然可以完美显示, 不会变形

## 文档和示例

[文档点我查看](https://dream2023.github.io/vue-image-pro/)
<br />
[在线示例点我查看](http://jsrun.net/x2XKp)

## Installation 安装

```bash
npm install vue-image-pro  --save
```

### Usage 用法

```js
// 全局 (推荐)
import ImagePro from 'vue-image-pro'

// 可以配置全局默认值
Vue.use(ImagePro, {
  src: '',
  color: '',
  username: '',
  backgroundColor: '',
  size: '',
  width: '',
  height: '',
  radius: '',
  mode: ''
})
```

```js
// 局部导入
// 这里注意要有 {} 括号
import { ImagePro } from 'vue-image-pro'

export default {
  ...
  components: {
    ImagePro
  },
  ...
}
```

```html
<image-pro :size="100" username="vue-image-pro" background-color="#123456" />
```

## Props

| 属性名          | 是否必填 |              默认值               | 类型   | 说明                                                         |
| --------------- | :------: | :-------------------------------: | ------ | ------------------------------------------------------------ |
| username        |    N     |             (空字符)              | String | 当 src 为空时,显示计算后用户名                               |
| src             |    N     |                 -                 | String | 图片链接                                                     |
| defaultSrc      |    N     |                 -                 | String | 默认图片                                                     |
| mode            |    N     |            aspectFill             | String | 图片展示模式(下有详细介绍)                                   |
| size            |    N     |                50                 | Number | 宽=高=size 值, 如设置 width 和 height 属性, 会覆盖 size 属性 |
| width           |    N     |                 -                 | Number | 图片宽度                                                     |
| height          |    N     |                 -                 | Number | 图片高度                                                     |
| color           |    N     |        根据背景色自动计算         | String | 字体颜色                                                     |
| backgroundColor |    N     |             随机颜色              | String | 背景颜色                                                     |
| isShowBgColor   |    N     |               false               | String | 当存在 src 时, 是否显示 backgroundColor 背景色               |
| radius          |    N     | 有图时默认为: 0, 无图时默认是: 50 | Number | 图片圆角                                                     |
| customStyle     |    N     |                {}                 | Object | 自定义样式                                                   |

### mode 值

| 值          | 说明                                                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------------------------------------ |
| aspectFill  | 保持纵横比缩放图片，只保证图片的短边能完全显示出来。也就是说，图片通常只在水平或垂直方向是完整的，另一个方向将会发生截取 |
| scaleToFill | 不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素                                                              |
| aspectFit   | 保持纵横比缩放图片，使图片的长边能完全显示出来。也就是说，可以完整地将图片显示出来                                       |
| widthFix    | 宽度不变，高度自动变化，保持原图宽高比不变                                                                               |
| heightFix   | 高度不变，宽度自动变化，保持原图宽高比不变                                                                               |

### 支持插槽

```html
<!-- 实例 -->
<image-pro>插槽</image-pro>
```

### 事件

| 事件名  | 说明         |
| ------- | ------------ |
| success | 图片加载成功 |
| error   | 图片加载失败 |
