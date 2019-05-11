<template>
  <div :style="bg" class="card" @click="onClick">
    {{number}}
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
        styles: 'background:#000'
      }
    },
    watch: {
      // background: 'setStyle' //采用watch的方式更新样式会出问题
    },
    mounted () {
      // this.setStyle()
    },
    methods: {
      setStyle () {
        this.styles = 'background:' + this.background
      },
      onClick () {
        this.$emit('onClick', this.number)
      }
    },
    computed: {
      bg: {
        get () {
          return 'background:' + this.background
        }
      }
    }
  }
</script>


<style>
  .card {
    text-align: center;
    /*color: white;*/
    width: 100%;
    height: 50px;
    line-height: 50px;
  }
</style>
