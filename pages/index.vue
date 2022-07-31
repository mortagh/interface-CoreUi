<template>
  <main>
    <div class="top-chart chart">
      <CardChart color="darkBlue" />
      <CardChart color="lightBlue" />
      <CardChart color="orangeYellow" />
      <CardChart color="salmon" />
    </div>
    <div class="mid-chart chart ma-0">
      <v-card flat rounded color="white" class="d-flex flex-no-wrap justify-space-between">
        <div>
          <v-card-title>Traffic</v-card-title>
          <v-card-subtitle>January 2021</v-card-subtitle>
        </div>

        <div class="allBtn ma-4">
          <v-btn-toggle v-model="date" class="mr-4">
            <v-btn value="day">
              <span class="hidden-sm-and-down">Day</span>
            </v-btn>

            <v-btn value="month">
              <span class="hidden-sm-and-down">Month</span>
            </v-btn>

            <v-btn value="year">
              <span class="hidden-sm-and-down">Year</span>
            </v-btn>
          </v-btn-toggle>

            <v-btn  icon tile class="pa-6 cloud-btn">
              <v-icon class="white--text">mdi-cloud-download-outline</v-icon>
            </v-btn>
        </div>
      </v-card>
      <LineChart :data="barChartData" :options="barChartOptions" height="100" />
    </div>
    <div class="mid-stats mb-6 px-5 py-2">
      <div class="mid-stat pa-1" v-for="(stat,i) in stats" :key="i">
        <p class="mb-1">{{ stat.title }}</p>
        <p class="mb-1 font-weight-bold">{{ stat.stat }}</p>
        <v-progress-linear rounded :value="stat.progress" class="mb-2" :color="stat.color"></v-progress-linear>
      </div>

    </div>
    <div class="networks">
      <CardNetwork :network="network" v-for="(network,i) in networks" :key="i" />
    </div>
  </main>
</template>

<script>
  import CardChart from '~/components/cardChart.vue';
  import CardNetwork from '~/components/cardNetwork.vue';
  import LineChart from '~/components/lineChart.vue';

  export default {
    name: "IndexPage",
    components: {
      LineChart,
      CardChart,
      CardNetwork,

    },
    data() {

      return {
        date:"month",

        //Stats
        stats: [{
            title: "Visits",
            stat: "29.703 Users (40%)",
            color: "facebookColor",
            progress: 40,
            color: "#2EB85C"
          },
          {
            title: "Unique",
            stat: "24.093 Users (20%)",
            color: "facebookColor",
            progress: 20,
            color: "#3399FF"
          },
          {
            title: "Pageviews",
            stat: "78.706 Users (60%)",
            color: "facebookColor",
            progress: 60,
            color: "#F9B115"
          },
          {
            title: "New Users",
            stat: "22.123 Users (80%)",
            color: "facebookColor",
            progress: 80,
            color: "#E55353"
          },
          {
            title: "Bounce Rate",
            stat: "Average Rate (40.15%)",
            color: "facebookColor",
            progress: 40.15,
            color: "#321FDB"
          }
        ],


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
            backgroundColor: "#E5E6E7",
            borderColor: "#3399FF",
            borderWidth: 2,
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
                display: true,
              },
            }, ],
            yAxes: [{
              ticks: {
                beginAtZero: true,
                max: 20,
                min: 0,
                stepSize: 5,
              },
              gridLines: {
                display: true,
              },
            }, ],
          },
        },

        // Networks stats
        networks: [{
          title: "Facebook",
          icon: "mdi-facebook",
          color: "facebookColor",
          to: "/",
          columnLeft: {
            number: "89k",
            title: "friends"
          },
          columnRight: {
            number: "489",
            title: "feeds"
          }
        }, {

          title: "Twitter",
          icon: "mdi-twitter",
          color: "twitterColor",
          to: "/",
          columnLeft: {
            number: "973k",
            title: "followers"
          },
          columnRight: {
            number: "1.792",
            title: "tweets"
          }
        }, {

          title: "linkedin",
          icon: "mdi-linkedin",
          color: "linkedinColor",
          to: "/",
          columnLeft: {
            number: "500",
            title: "contacts"
          },
          columnRight: {
            number: "1.292",
            title: "feeds"
          }
        }, ]
      }
    }
  }

</script>

<style scoped>
  main {
    padding: 24px;
  }

  .chart {
    margin: 24px 0;
    gap: 24px;
    width: 100%;
  }

  .top-chart {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .mid-stats {
    display: flex;
    justify-content: space-around;
    gap: 20px;
    text-align: center;
    background-color: #F7F7F8;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
  }

  .mid-stat {
    width: 100%;
  }

  .mid-chart {
    background-color: white;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
  }

  .networks {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
  .cloud-btn{
    background-color: #321fdb;
    border-radius: 4px;
  }

</style>
