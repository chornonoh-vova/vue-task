<template>
  <div id="app">
    <page-header/>
    <filter-header/>
    <div class="items">
      <template v-for="item of items">
        <basket-card class="card" v-if="item.type === 'basket'" :key="item.id" :item="item"/>
        <bot-card class="card" v-if="item.type === 'bot'" :key="item.id" :item="item"/>
      </template>
    </div>
  </div>
</template>

<script>
import BasketCard from './components/cards/BasketCard.vue'
import BotCard from './components/cards/BotCard.vue'
import FilterHeader from './components/FilterHeader.vue'
import PageHeader from './components/PageHeader.vue'

function randomGraph (points) {
  const arr = Array(points).fill(0)

  for (let i = 0; i < points; i++) {
    arr[i] = {
      x: i,
      y: Math.floor(Math.random() * Math.floor(100))
    }
  }

  return arr
}

export default {
  name: 'App',
  components: {
    FilterHeader,
    PageHeader,
    BasketCard,
    BotCard
  },
  data () {
    return {
      items: [
        {
          id: 1,
          type: 'basket',
          name: 'BG 6 Basket',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        },
        {
          id: 2,
          type: 'basket',
          name: 'BG 8',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        },
        {
          id: 3,
          type: 'basket',
          name: 'BG 6 Index',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        },
        {
          id: 4,
          type: 'basket',
          name: 'BG 6 Index',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        },
        {
          id: 5,
          type: 'bot',
          name: 'Bedrock Trend',
          icon: 'bedrock',
          pnl: 1.521,
          perMonth: 82,
          graph: randomGraph(20),
          frequency: 1,
          riskLevel: 1
        },
        {
          id: 6,
          type: 'bot',
          name: 'MoonBot BTC',
          icon: 'bedrock',
          pnl: 1.521,
          perMonth: 82,
          graph: randomGraph(20),
          frequency: 1,
          riskLevel: 1
        },
        {
          id: 7,
          type: 'bot',
          name: 'Samurai Scalp',
          icon: 'samurai',
          pnl: 1.521,
          perMonth: 82,
          graph: randomGraph(20),
          frequency: 1,
          riskLevel: 1
        },
        {
          id: 8,
          type: 'bot',
          name: 'Wavebased LFT ETH',
          icon: 'wavebased',
          pnl: 1.521,
          perMonth: 82,
          graph: randomGraph(20),
          frequency: 1,
          riskLevel: 1
        },
        {
          id: 9,
          type: 'basket',
          name: 'BG 6 Basket',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        },
        {
          id: 10,
          type: 'basket',
          name: 'BG 8',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        },
        {
          id: 11,
          type: 'basket',
          name: 'BG 6 Index',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        },
        {
          id: 12,
          type: 'basket',
          name: 'BG 6 Index',
          pnl: 34.78,
          currencies: {
            btc: 16.5,
            eth: 16.5,
            xrp: 16.5,
            usdt: 16.5,
            bch: 16.5,
            ltc: 16.5,
            other: 1
          }
        }
      ]
    }
  }
}
</script>

<style lang="scss">
@mixin font($font-family, $font-file) {
  @font-face {
    font-family: $font-family;
    src: url($font-file+'.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
  }
}

@include font('VisueltPro Regular', './assets/fonts/VisueltPro-Regular');

#app {
  background: linear-gradient(0deg, #EFF1F7 54.35%, rgba(245, 246, 250, 0.46) 98.23%);
  border-radius: 12px;
  padding-top: 40px;
  padding-bottom: 40px;
}

.items {
  margin: 40px 60px 0px 60px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
}

.card {
  flex: 1 0 21%;
  width: 280px;
  height: 370px;
  margin-bottom: 32px;
  margin-right: 28px;
}

.card:hover {
  box-shadow: 0px 4px 19px rgba(81, 81, 189, 0.19);
}
</style>
