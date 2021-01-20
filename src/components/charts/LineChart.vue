<script>
import { Line } from 'vue-chartjs'

export default {
  extends: Line,
  props: ['data'],
  computed: {
    chartData: function () {
      return this.data
    }
  },

  mounted () {
    this.renderLineChart()
  },

  watch: {
    data: function () {
      this.renderLineChart()
    }
  },

  methods: {
    renderLineChart () {
      this.renderChart(this.chartData, {
        responsive: true,
        maintainAspectRatio: false,
        title: {
          display: false
        },
        legend: {
          display: false
        },
        tooltips: {
          enabled: false
        },
        scales: {
          xAxes: [{
            type: 'linear',
            display: false
          }],
          yAxes: [{
            type: 'linear',
            display: false
          }]
        },
        elements: {
          line: {
            tension: 0
          },
          point: {
            radius: 0
          }
        }
      })
    }
  }
}
</script>

<style>
</style>
