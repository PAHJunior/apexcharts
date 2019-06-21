<template>
  <q-page class="flex flex-center">
    <div>
      <q-card dark bordered class="text-primary">
        <q-card-section>
          <div class="text-h6">Grafico de linha</div>
          <q-btn @click="updateChart" icon="check"/>
        </q-card-section>

        <q-separator dark inset />

        <q-card-section>
          <apexchart width="580" type="line" height=350 :options="options" :series="series" />
        </q-card-section>
      </q-card>
    </div>
  </q-page>

</template>

<style>
#chart{
  height: 50%;
  width: 50%;
}
</style>

<script>
import ApexCharts from 'apexcharts'
import VueApexCharts from 'vue-apexcharts'

export default {
  name: 'PageIndex',
  components: {
    apexchart: VueApexCharts,
  },
  data() {
    return {
      lorem: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      options: {
        chart: {
          
        },
        xaxis: {
          categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998],
        },
      },
      series: [{
        name: 'Total',
        data: [30, 40, 45, 50, 49, 60, 70, 81]
      }],
      theme: {
        monochrome: {
          enabled: true,
          color: '#255aee',
          shadeTo: 'light',
          shadeIntensity: 0.65
        }
      }
    }
  },
  methods: {
    updateChart() {
      const max = 90;
      const min = 20;
      const newData = this.series[0].data.map(() => {
        return Math.floor(Math.random() * (max - min + 1)) + min
      })
      // In the same way, update the series option
      this.series = [{
        data: newData
      }]
    }
  }
}
</script>
