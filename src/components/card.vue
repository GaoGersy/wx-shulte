<template>
  <div :style="styles" class="card" @click="onClick">
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
      background: 'setStyle'
    },
    mounted () {
      this.setStyle()
    },
    methods: {
      setStyle () {
        this.styles = 'background:' + this.background
      },
      onClick () {
        this.$emit('onClick', this.number)
      }
    }
  }
</script>


<style>
  .card {
    text-align: center;
    color: white;
    width: 100%;
    height: 50px;
    line-height: 50px;
  }
</style>
