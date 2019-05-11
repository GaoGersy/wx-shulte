<template>
  <div style="width: 100%">
    <Timer></Timer>
    <Schulte :count="count" :needRemoveNumber="needRemoveNumber" ></Schulte>
<!--    :color1="color1" :color2="color2"-->
  </div>
</template>

<script>
  import Schulte from '@/components/Schulte'
  import Timer from '@/components/Timer'

  export default {
    data () {
      return {
        count: 7,
        needRemoveNumber: false,
        color1: '#90ff8e',
        color2: '#3abc51'
      }
    },
    props: {},
    mounted () {
    },
    components: {
      Schulte,
      Timer
    },
    methods: {},
    created () {
      // let app = getApp()
    }
  }
</script>

<style scoped>
</style>
