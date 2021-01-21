<template>
  <button :class="{colored}" @click="onClick">
    {{text}}
  </button>
</template>

<script>
export default {
  props: ['colored', 'text'],
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
  justify-content: space-around;
  padding: 9px 16px;
  font-family: VisueltPro Regular;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 18px;
  height: 34px;
  background: #fff;
  color: #959CBD;
  border: 1px solid #fff;
  border-radius: 4px;
}

.colored {
  color: #fff;
  background: #4A4AE2;
  border: 1px solid#4A4AE2;
}

@media (max-width: 840px) {
  button {
    display: none;
  }

  .colored {
    display: flex;
  }
}

@media (max-width: 550px) {
  .colored {
    display: none;
  }
}
</style>
