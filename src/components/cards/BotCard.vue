<template>
  <div class="card" @mouseenter="hover()" @mouseleave="unhover()">
    <div class="card-head">
      <p class="card-head-pricing">
        From ${{item.perMonth}}/mo
      </p>
      <span class="spacer"></span>
      <img class="card-head-img" src="../../assets/icons/trade.svg" alt="Trade">
      <p class="card-head-time">
        2 months
      </p>
    </div>
    <img class="card-logo" :src="logoIcon(item.icon)" alt="Logo icon">
    <h3 class="card-header">{{item.name}}</h3>
    <div class="card-chart">
      <line-chart :styles="{height: '70px'}" :data="graphData()" />
    </div>
    <div class="card-pnl">
      <p class="card-pnl-text">Period PnL</p>
      <p class="card-pnl-percentage">{{item.pnl}} %</p>
    </div>
    <div class="card-footer" :style="{display: hovered ? 'flex' : 'none'}">
      <frequency-indicator :num="item.frequency"/>
      <risk-indicator :num="item.riskLevel"/>
    </div>
  </div>
</template>

<script>
import LineChart from '../charts/LineChart.vue'
import FrequencyIndicator from '../indicators/FrequencyIndicator.vue'
import RiskIndicator from '../indicators/RiskIndicator.vue'

export default {
  components: { LineChart, FrequencyIndicator, RiskIndicator },
  props: ['item'],
  data () {
    return {
      hovered: false
    }
  },
  methods: {
    hover () {
      this.hovered = true
    },
    unhover () {
      this.hovered = false
    },
    graphData () {
      if (this.hovered) {
        return {
          datasets: [{
            backgroundColor: '#fff',
            borderColor: '#4A4AE2',
            data: this.item.graph
          }]
        }
      } else {
        return {
          datasets: [{
            backgroundColor: '#fff',
            borderColor: '#959CBD',
            data: this.item.graph
          }]
        }
      }
    },
    logoIcon (icon) {
      return require('@/assets/icons/logos/' + icon + '.svg')
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
  &-head {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: space-between;
    align-items: center;
    align-self: stretch;
    padding: 15px 25px;
    &-pricing {
      font-family: VisueltPro Regular;
      font-style: normal;
      font-weight: 500;
      font-size: 10px;
      line-height: 13px;
      color: #4A4AE2;
    }
    &-img {
      margin-right: 10px;
    }
    &-time {
      font-family: VisueltPro Regular;
      font-style: normal;
      font-weight: 500;
      font-size: 10px;
      line-height: 13px;
      color: #959CBD;
    }
  }
  &-header {
    font-family: VisueltPro Regular;
    font-style: normal;
    font-weight: normal;
    font-size: 26px;
    line-height: 33px;
    text-align: center;
    color: #3C3463;
    width: 144px;
  }
  &-chart {
    max-width: 202px;
    max-height: 70px;
  }
  &-pnl {
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
  &-footer {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-self: stretch;
    margin-left: 40px;
    margin-right: 40px;
    margin-bottom: 20px;
  }
}
.spacer {
  flex: 1 1 30%;
}
</style>
