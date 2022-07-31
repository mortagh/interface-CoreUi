<template>
  <v-card outlined :color="chart.color" class="card-chart">
    <div class="d-flex flex-no-wrap justify-space-between">

      <div>
        <v-card-title class="text-h5 white--text">{{chart.number}} <span class="subtitle-1">{{chart.percent}}<v-icon
              class="white--text">
              mdi-arrow-{{chart.arrow}}-right-thin</v-icon>)</span></v-card-title>

        <v-card-subtitle class="mb-0 pb-0 white--text">{{ chart.title }}</v-card-subtitle>
      </div>


      <v-menu flat offset-y transition="scale-transition">
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on" class="ma-2">
            <v-icon class="white--text">mdi-dots-vertical</v-icon>
          </v-btn>
        </template>
        <v-list class="d-flex flex-column">
            <v-btn text class="ma-1">Action</v-btn>
            <v-btn text class="ma-1">Action</v-btn>
            <v-btn text class="ma-1">Action</v-btn>

        </v-list>
      </v-menu>

    </div>

    <v-card-actions class="d-flex justify-center" v-if="chart.type=='bar'">
      <Bar-chart :data="chart.barChartData" :options="chart.barChartOptions" height="100" />
    </v-card-actions>
    <v-card-actions class="d-flex justify-center" v-if="chart.type=='line'">
      <Line-chart :data="chart.barChartData" :options="chart.barChartOptions" height="100" />
    </v-card-actions>

  </v-card>
</template>

<script>
  import Color from '~/pages/color.vue';
  import BarChart from './barChart.vue';
  import LineChart from './lineChart.vue';
  export default {
    props: {
      chart: Object,
    },
    components: {
      Color,
      BarChart,
      LineChart
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
    max-width: calc(25% - 24px);
  }

</style>
