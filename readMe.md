## 介绍
一个可以根据文字直接生成对应logo的vue组件

## 使用方式
1. 将文件引入到项目中
2. 像普通单文件组件一样使用即可。

## 举个例子
```
// 父组件
<template>
  <div class="page-template-group">
    <canvas-avatar :options="options"></canvas-avatar>
  </div>
</template>

<script>
  import CanvasAvatar from '@/src/components/canvasAvatar'

  export default {
    components: {
      CanvasAvatar
    },
    data () {
      return {
        options: {
          text: 'T'
          color: '#333'
        }
      }
    }
  }
</script>
```
效果如下：

![image](https://user-images.githubusercontent.com/6983075/41338443-cc2372ca-6f24-11e8-95b8-0b1bf201ceda.png)