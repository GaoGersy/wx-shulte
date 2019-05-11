<template>
  <div style="width: 100%">
    <div class="grid" :style="style">
      <card v-for="item in items" :key="item.number" :number="item.number" :background="item.background"
            @onClick="onClick"></card>
    </div>
  </div>
</template>

<script>
  import card from '@/components/card'
  // import {MessageBox} from 'mint-ui'

  export default {
    data () {
      return {
        items: [],
        numbers: [],
        style: '',
        currentNumber: 1,
        needRemoveNumber: true,
        totalCount: 7
      }
    },
    props: {
      count: {
        type: Number,
        default: 4
      },
      needRemoveNumber: {
        type: Boolean,
        default: true
      },
      color1: {
        type: String,
        default: '#48d6ff'
      },
      color2: {
        type: String,
        default: '#345cff'
      }
    },
    mounted () {
      this.init()
    },
    components: {
      card
    },
    methods: {
      init () {
        let count = this.count
        this.totalCount = count * count
        let style = 'grid-template-columns:'
        let percent = (100 / count) + '% '
        for (let i = 0; i < count; i++) {
          style += percent
        }
        this.style = style + ';'
        this.initData(count)
      },
      initData (row) {
        let totalCount = this.totalCount
        let color1 = this.color1
        let color2 = this.color2
        let num = 0
        let index = 0
        for (let i = 1; i <= totalCount; i++) {
          let color
          if (index % row === 0) {
            num = num === 1 ? 2 : 1
            color1 = num === 2 ? this.color1 : this.color2
            color2 = num === 1 ? this.color1 : this.color2
            index = 0
          }
          if (index % 2 === 0) {
            color = color1
          } else {
            color = color2
          }
          index++
          let number = this.getNumber(totalCount)
          let item = {
            number: number,
            background: color
          }
          this.items.push(item)
        }
      },
      getNumber (totalCount) {
        let number = Math.floor((Math.random() * totalCount) + 1)
        let numbers = this.numbers
        if (numbers.indexOf(number) > -1) {
          return this.getNumber(totalCount)
        } else {
          numbers.push(number)
          return number
        }
      },
      onClick (number) {
        if (this.currentNumber === number) {
          this.currentNumber++
          if (this.needRemoveNumber) {
            this.removeNumber(number)
          }
          if (this.currentNumber > this.totalCount) {
            // MessageBox.alert('Success!')
            //   .then(action => {
            //     this.init()
            //   })
          }
        }
      },
      removeNumber (number) {
        let items = this.items
        for (let i in items) {
          let item = items[i]
          if (item.number === number) {
            item.number = ''
          }
        }
      }
    },
    created () {
      // let app = getApp()
    }
  }
</script>

<style scoped>
  .grid {
    display: grid;
  }
</style>
