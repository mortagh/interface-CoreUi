<template>
  <v-card outlined :color="color" class="card-chart">
    <div class="d-flex flex-no-wrap justify-space-between">

      <div>
        <v-card-title class="text-h5 white--text">26k <span class="subtitle-1">(-12,4%<v-icon class="white--text">
              mdi-arrow-top-right-thin</v-icon>)</span></v-card-title>

        <v-card-subtitle class="mb-0 pb-0 white--text">Users</v-card-subtitle>
      </div>

      <v-btn icon class="ma-2">
        <v-icon class="white--text">mdi-dots-vertical</v-icon>
      </v-btn>

    </div>

    <v-card-actions class="d-flex justify-center">
      <Bar-chart :data="barChartData" :options="barChartOptions" height="100" width="200"  />
    </v-card-actions>

  </v-card>
</template>

<script>
  import Color from '~/pages/color.vue';
  import BarChart from './barChart.vue';
  export default {
    props: {
      color: String,
    },
    components: {
      Color,
      BarChart
    },
    data() {
      return {

        // Traffic Chart
        barChartData: {
          labels: [
            "January",
            "February",
            "March",
            "April",
            "May",
            "Jun",
            "july",
          ],
          datasets: [{
            label: "Visualizaciones",
            data: [2, 1, 16, 3, 4, 5, 0],
            backgroundColor: "transparent",
            borderColor: "white",
            borderWidth: 1,
          }, ],
        },
        barChartOptions: {
          responsive: true,
          legend: {
            display: false,
          },
          tooltips: {
            backgroundColor: "#17BF62",
          },
          scales: {
            xAxes: [{
              gridLines: {
                display: false,
              },
              ticks: {
                display: false
              },
            }, ],
            yAxes: [{
              ticks: {
                display: false
              },
              gridLines: {
                display: false,
              },
            }, ],
          },
        }
      }
    },

  }

</script>

<style>
  .graphique {
    width: 100%;
    min-height: 100px;
    background-color: white;
  }

  .card-chart {
    min-width: calc(25% - 24px);
  }

</style>
