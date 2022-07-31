<template>
  <div class="card-network">
    <v-card outlined class="card-network card-icon ma-0 pa-0" :color="network.color" height="150">
      <v-btn icon class="ma-auto">
        <v-icon class="white--text" size="65">{{network.icon}}</v-icon>
      </v-btn>
    </v-card>
    <v-card outlined class="number-network ma-0 pa-0" height="100">

      <div class="countainer-number text-uppercase pa-2">

        <div class="column column-left">
          <v-card-title class="">
            {{network.columnLeft.number}}
          </v-card-title>
          <v-card-subtitle class="">
            {{network.columnLeft.title}}
          </v-card-subtitle>
        </div>

        <div class="split"></div>

        <div class="column column-right">
          <v-card-title class="">
            {{network.columnRight.number}}
          </v-card-title>
          <v-card-subtitle class="">
            {{network.columnRight.title}}
          </v-card-subtitle>
        </div>

      </div>

    </v-card>
  </div>

</template>

<script>
  export default {
    name: "cardNetworks",
    props: {
      network: [],
    },
    // components: {
    //   network
    // }
  }

</script>

<style>
  .column{
    height: 100%;
  }

  .countainer-number{
    height: 100%;
    display: flex;
    justify-content: space-around;
  }

  .split{
    width: 1px;
    height: 100%;
    background-color: grey;
  }


  .card-network {
    min-width: calc(33% - 24px);
    border-bottom-left-radius: 0 !important;
    border-bottom-right-radius: 0 !important;
  }

  .card-icon {
    display: flex;
  }

  .number-network {
    border-top-left-radius: 0 !important;
    border-top-right-radius: 0 !important;
  }

</style>
