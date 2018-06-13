<template>
  <div class="component-avatar">
    <canvas ref="canvasEle" class="canvas-avatar hidden" :width="mergeOptions.width" :height="mergeOptions.height"></canvas>
    <img :src="image" alt="">
  </div>
</template>

<script>
export default {
  props: {
    options: {
      type: Object,
      required: false
    }
  },
  data () {
    return {
      width: 100,
      height: 100,
      image: '',
      initOptions: {
        text: 'hello',
        width: 100,
        height: 100,
        fontSize: 20,
        fontFamily: '微软雅黑',
        color: '#FFF',
        background: '#eee',
        textAlign: 'center',
        textBaseline: 'middle',
        pos: [50, 50]
      }
    }
  },
  computed: {
    mergeOptions () {
      return Object.assign({}, this.initOptions, this.options)
    }
  },
  watch: {
    mergeOptions (val, oldVal) {
      this.$nextTick(() => {
        this.renderImg()
      })
    }
  },
  methods: {
    init () {
      this.renderImg()
    },
    drawRect () {
      let options = this.mergeOptions
      let ele = this.$refs['canvasEle']
      let ctx = ele.getContext('2d')
      ctx.fillStyle = options.background
      ctx.fillRect(0, 0, options.width, options.height)

      ctx.font = `${options.fontSize}px ${options.fontFamily}`
      ctx.fillStyle = options.color
      ctx.textAlign = options.textAlign
      ctx.textBaseline = options.textBaseline
      ctx.fillText(options.text, options.pos[0], options.pos[1])
    },
    canvasToImgUrl () {
      let url = this.$refs['canvasEle'].toDataURL()
      this.image = url
    },
    renderImg () {
      this.drawRect()
      this.canvasToImgUrl()
    }
  },
  mounted () {
    this.init()
  }
}
</script>

<style lang="scss" scoped>
  .component-avatar {
    position: relative;

    .hidden {
      display: none;
    }
  }
</style>
