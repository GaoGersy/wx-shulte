<template>
  <div class="timer">
    {{time}}
  </div>
</template>

<script>
  export default {
    props: {
      number: String,
      background: String
    },
    data () {
      return {
        styles: 'background:#000',
        currentTime: 0,
        time: '0 s',
        interval: null
      }
    },
    watch: {
      background: 'setStyle'
    },
    mounted () {
      this.initEvent()
    },
    methods: {
      initEvent () {
        this.interval = setInterval(() => {
          this.updateTime()
        }, 1000)
      },
      updateTime () {
        this.time = (this.currentTime++) + ' s'
      },
      setStyle () {
        this.styles = 'background:' + this.background
      },
      onClick () {
        this.$emit('onClick', this.number)
      }
    },
    beforeDestroy () {
      this.interval.clear()
    }
  }
</script>


<style>
  .timer {
    background: #49c4c7;
    text-align: center;
    color: white;
    width: 100%;
    height: 30px;
    line-height: 30px;
  }
</style>
