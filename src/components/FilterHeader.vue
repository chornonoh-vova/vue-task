<template>
  <div class="filter">
    <filter-button class="filter-button"/>
    <small-button class="filter-small" :colored="type === 'all'" text="All" @clicked="onFilter('all')"/>
    <small-button class="filter-small" :colored="type === 'basket'" text="Baskets" @clicked="onFilter('basket')"/>
    <small-button class="filter-small" :colored="type === 'bot'" text="Bots" @clicked="onFilter('bot')"/>
    <small-button class="filter-small" :colored="type === 'coming soon'" text="Coming soon"/>
    <div class="spacer"></div>
    <sort-by-button class="filter-small" @clicked="onOrderBy()" :order="order"/>
    <all-time-button/>
  </div>
</template>

<script>
import AllTimeButton from './buttons/AllTimeButton.vue'
import FilterButton from './buttons/FilterButton.vue'
import SmallButton from './buttons/SmallButton.vue'
import SortByButton from './buttons/SortByButton.vue'
export default {
  components: { FilterButton, SmallButton, AllTimeButton, SortByButton },
  data () {
    return {
      type: 'all',
      order: 'none'
    }
  },
  methods: {
    onFilter (type) {
      this.type = type
      this.$emit('filter', type)
    },
    onOrderBy () {
      if (this.order === 'none') {
        this.order = 'pnl'
      } else {
        this.order = 'none'
      }
      this.$emit('order', this.order)
    }
  }
}
</script>

<style lang="scss" scoped>
.filter {
  margin: 40px 60px 20px 60px;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  &-button {
    margin-right: 32px;
  }
  &-small {
    margin-right: 10px;
  }
}

.spacer {
  flex-grow: 1;
}

@media (max-width: 320px) {
  .filter {
    margin: 40px 12px 20px 12px;
  }
}
@media (max-width: 375px) {
  .filter {
    margin: 40px 20px 20px 20px;
  }
}
</style>
