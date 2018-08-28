<template>
  <div class="vital-chart-wx">
    <div>wx-echarts</div>
    <div class="my-charts">
      <ec-canvas  class="canvas" id="mychart" canvas-id="mychart-bar" :ec="ec"></ec-canvas>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['options'],
    data () {
      return {
        ec: {
          options: this.options
        }
      }
    },
    watch: {
      options: {
        handler (newValue, oldValue) {
          this.getOptions(newValue)
        },
        deep: true
      }
    },
    created () {
    },
    mounted () {
    },
    methods: {
      getOptions: function (newValue) {
        this.ec.options = newValue
      }
    }
  }
</script>

<style>
  .my-charts{
    height: 500px;
  }
  ec-canvas {
    width: 300px;
    height: 300px;
  }
</style>
