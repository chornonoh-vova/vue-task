<template>
  <div class="card">
    <h3 class="card-header">{{item.name}}</h3>
    <div class="card-chart">
      <doughnut-chart :data="chartData" />
      <p class="card-chart-text" v-if="chartTextDisplay">{{chartPercentage}}<span class="card-chart-text-percentage">%</span></p>
    </div>
    <div class="card-pnl">
      <p class="card-pnl-text">Period PnL</p>
      <p class="card-pnl-percentage">{{item.pnl}} %</p>
    </div>
    <div class="card-icons">
      <div class="card-icons-item" v-for="(value, name) in item.currencies" :key="name">
        <img :src="currencyIcon(name)" @mouseenter="displayChartText(value)" @mouseleave="removeChartText()" alt="Currency icon">
      </div>
    </div>
  </div>
</template>

<script>
import DoughnutChart from '../charts/DoughnutChart.vue'

const colorsByCurrency = {
  btc: '#F7931A',
  eth: '#627EEA',
  xrp: '#3B536C',
  usdt: '#26A17B',
  bch: '#8DC351',
  ltc: '#BFBBBB',
  other: '#F5F6FA'
}

export default {
  components: { DoughnutChart },
  props: ['item'],
  data () {
    return {
      chartPercentage: 0,
      chartTextDisplay: false
    }
  },
  computed: {
    chartData () {
      return {
        datasets: [{
          data: Object.values(this.item.currencies),
          backgroundColor: Object.entries(this.item.currencies).map(([k, v]) => colorsByCurrency[k]),
          hoverBorderColor: Object.entries(this.item.currencies).map(([k, v]) => colorsByCurrency[k]),
          label: 'Dataset',
          borderWidth: 1,
          hoverBorderWidth: 2
        }]
      }
    }
  },
  methods: {
    currencyIcon (icon) {
      return require('@/assets/icons/currencies/' + icon + '.svg')
    },
    displayChartText (value) {
      this.chartPercentage = value
      this.chartTextDisplay = true
    },
    removeChartText () {
      this.chartTextDisplay = false
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  background: #ffffff;
  border-radius: 8px;
  min-width: 280px;
  display: flex;
  flex-direction: column;
  align-items: center;
  &-header {
    font-family: VisueltPro Regular;
    font-style: normal;
    font-weight: normal;
    font-size: 26px;
    line-height: 33px;
    text-align: center;
    color: #3C3463;
    margin-top: 30px;
  }
  &-chart {
    position: relative;
    width: 120px;
    height: 120px;
    &-text {
      position: absolute;
      top: 32%;
      left: 52%;
      transform: translate(-50%, -50%);
      font-family: VisueltPro Regular;
      font-style: normal;
      font-weight: normal;
      font-size: 26px;
      line-height: 33px;
      color: #3C3463;
      &-percentage {
        font-family: VisueltPro Regular;
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 18px;
      }
    }
  }
  &-pnl {
    margin-top: 40px;
    text-align: center;
    &-text {
      margin: 0;
      font-family: VisueltPro Regular;
      font-style: normal;
      font-weight: 500;
      font-size: 10px;
      line-height: 13px;
      color: #959CBD;
    }
    &-percentage {
      margin: 0;
      font-family: VisueltPro Regular;
      font-style: normal;
      font-weight: normal;
      font-size: 26px;
      line-height: 33px;
      color: #5EAF61;
    }
  }
  &-icons {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin: 18px 44px;
    width: 70%;
    &-item {
      width: 18px;
      height: 18px;
    }
  }
}
</style>
