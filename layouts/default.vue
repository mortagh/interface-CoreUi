<template>
  <v-app>
    <Navigation ref="drawer"/>
    <Header @toggle-drawer="$refs.drawer.drawer = !$refs.drawer.drawer"/>
    <v-main >
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer
      :absolute="!fixed"
      app
    >
    </v-footer>
  </v-app>
</template>

<script>
import Header from '~/components/header.vue'
import navigation from '~/components/navigation.vue'
export default {
  components: { navigation, Header },
  name: 'DefaultLayout',
  data () {
    return {
      fixed: false,
    }
  }
}
</script>

<style>
  .v-main{
    background-color: #EBEDEF ;
  }
</style>
