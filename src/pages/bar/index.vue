<template>
  <div class="counter-warp">
    <button @click="changeEcharts">切换</button>
    <wx-echarts :options = 'wxOptions'></wx-echarts>
    <!--<div class="container">-->
      <!--<ec-canvas class="canvas" id="mychart-dom-bar" canvas-id="mychart-bar" :ec="ec"></ec-canvas>-->
    <!--</div>-->
  </div>
</template>

<script>
import wxEcharts from '../../component/wx-echarts'

const data = [
  [1290, 1330, 1320, 820, 932, 901, 934],
  [934, 934, 934, 934, 934, 932, 901]
]
let i = 0

export default {
  components: {
    wxEcharts
  },
  data () {
    return {
      wxOptions: this.getOptions(0)
    }
  },
  mounted () {
  },
  methods: {
    changeEcharts: function () {
      if (i) {
        i = 0
      } else {
        i = 1
      }
      setTimeout(() => {
        this.wxOptions = this.getOptions(i)
      }, 3000)
    },
    getOptions: function (i) {
      let option = {
        xAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
          type: 'value'
        },
        series: [{
          data: data[i],
          type: 'line'
        }]
      }
      return option
    }
  }
}
</script>

<style>

</style>
