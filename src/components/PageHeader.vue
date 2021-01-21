<template>
  <header class="header">
    <h1 class="header-text">Strategy Marketplace</h1>
    <big-button text="Compare" icon="compare.svg" class="header-compare"/>
    <big-button text="Help me decide" :colored="true" class="header-decide"/>
  </header>
</template>

<script>
import BigButton from './buttons/BigButton.vue'

export default {
  components: {
    BigButton
  }
}
</script>

<style lang="scss" scoped>
.header {
  margin: 0px 60px 20px 60px;
  display: flex;
  align-items: center;
  flex-direction: row;
  flex-wrap: nowrap;
  &-text {
    flex-grow: 10;
    font-family: VisueltPro Regular;
    font-style: normal;
    font-weight: normal;
    font-size: 32px;
    line-height: 120%;
    color: #3C3463;
    margin: 0;
  }
  &-compare {
    width: 160px;
    flex-grow: 1;
  }
  &-decide {
    margin-left: 12px;
    width: 160px;
    flex-grow: 1;
  }
}

@media (max-width: 550px) {
  .header-decide {
    display: none;
  }
}

@media (max-width: 320px) {
  .header {
    margin: 0px 12px 20px 12px;
  }
  .header-compare {
    display: none;
  }
}

@media (max-width: 375px) {
  .header {
    margin: 0px 20px 20px 20px;
  }
}
</style>
