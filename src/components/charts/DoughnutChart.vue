<script>
import { Doughnut } from 'vue-chartjs'

export default {
  extends: Doughnut,
  props: ['data'],
  mounted () {
    this.renderChart(this.data, {
      responsive: true,
      title: {
        display: false
      },
      legend: {
        display: false
      },
      tooltips: {
        enabled: false
      },
      cutoutPercentage: 92
    })
  }
}
</script>

<style>
</style>
