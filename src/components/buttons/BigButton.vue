<template>
  <button :class="{colored}">
    <template v-if="icon !== undefined">
      <img :src="getIcon(icon)" alt="Icon">
    </template>
    {{text}}
  </button>
</template>

<script>
export default {
  props: ['text', 'icon', 'colored'],
  methods: {
    getIcon (icon) {
      return require('@/assets/icons/' + icon)
    }
  }
}
</script>

<style lang="scss" scoped>
button {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
  padding: 9px 16px;
  font-family: VisueltPro Regular;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 18px;
  max-width: 160px;
  height: 42px;
  background: #fff;
  color: #959CBD;
  border: 1px solid #CED2E5;
  border-radius: 4px;
}

.colored {
  background: #4A4AE2;
  color: #FFFFFF;
  border: 1px solid #4A4AE2;
}
</style>
