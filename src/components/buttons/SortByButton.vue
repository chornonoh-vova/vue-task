<template>
  <button @click="onClick">
    Sort by: {{text}}
  </button>
</template>

<script>
const orderDict = {
  pnl: 'PnL',
  none: 'None'
}

export default {
  props: ['order'],
  computed: {
    text () {
      return orderDict[this.order]
    }
  },
  methods: {
    onClick () {
      this.$emit('clicked')
    }
  }
}
</script>

<style lang="scss" scoped>
button {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 8px 12px;
  justify-content: space-around;
  font-family: VisueltPro Regular;
  font-style: normal;
  font-weight: 500;
  font-size: 12px;
  line-height: 15px;
  width: 100px;
  height: 34px;
  background: #fff;
  color: #959CBD;
  border: 1px solid #CED2E5;
  border-radius: 4px;
}
</style>
