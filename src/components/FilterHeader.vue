<template>
  <div class="filter">
    <filter-button class="filter-button"/>
    <small-button class="filter-small" :colored="true" text="All"/>
    <small-button class="filter-small" :colored="false" text="Baskets"/>
    <small-button class="filter-small" :colored="false" text="Bots"/>
    <small-button class="filter-small" :colored="false" text="Coming soon"/>
    <div class="spacer"></div>
    <sort-by-button class="filter-small"/>
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
      type: '',
      order: ''
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
</style>
