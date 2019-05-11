<template>
  <div style="width: 100%">
    <div
      style="background: #1a96c0;line-height: 30px;border-radius: 3px;width: 30px;color:#a6f5ff;margin-left:5px;height: 30px;text-align: center;display: inline-block"
      v-for="item in buttons" :key="item"
      @click="changeLevel(item)">{{item}}
    </div>
    <Timer :count="trainCount"></Timer>
    <Schulte :count="count" :needRemoveNumber="needRemoveNumber" @onComplete="onComplete"></Schulte>
    <!--    :color1="color1" :color2="color2"-->
  </div>
</template>

<script>
  import Schulte from '@/components/Schulte'
  import Timer from '@/components/Timer'

  export default {
    data () {
      return {
        trainCount: 0,
        count: 10,
        needRemoveNumber: true,
        color1: '#90ff8e',
        color2: '#3abc51',
        buttons: [
          3, 4, 5, 6, 7, 8, 9, 10
        ]
      }
    },
    props: {},
    mounted () {
    },
    components: {
      Schulte,
      Timer
    },
    methods: {
      onComplete () {
        this.trainCount++
      },
      changeLevel (level) {
        this.count = level
        this.trainCount++
      }
    },
    created () {
      // let app = getApp()
    }
  }
</script>

<style scoped>
</style>
