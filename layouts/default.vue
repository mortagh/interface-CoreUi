<template>
  <v-app>
    <Navigation />
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-spacer />
    </v-app-bar>
    <v-main>
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
import navigation from '~/components/navigation.vue'
export default {
  components: { navigation },
  name: 'DefaultLayout',
  data () {
    return {
      drawer: false,
      clipped: false,
      fixed: false,
      right: true,
      rightDrawer: false,
    }
  }
}
</script>
