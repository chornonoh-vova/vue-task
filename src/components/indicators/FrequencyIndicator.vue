<template>
  <div class="indicator">
    <b class="indicator-text">Frequency</b>
    <div class="indicator-items">
      <template v-for="number in 4">
        <div class="indicator-item" :class="{active: number <= num}" :key="number"></div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  props: ['num']
}
</script>

<style lang="scss" scoped>
.indicator {
  display: flex;
  flex-direction: column;
  align-items: center;
  &-text {
    font-family: VisueltPro Regular;
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 15px;
    color: #000000;
  }
  &-items {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  &-item {
    width: 13px;
    height: 3px;
    margin: 4px;
    background: #CED2E5;
    opacity: 0.5;
    border-radius: 1px;
  }
}
.active {
  opacity: 1;
  background: #4A4AE2;
}
</style>
