<template>
  <v-app-bar :clipped-left="clipped" fixed app flat class="white">
    <v-app-bar-nav-icon class="text-header" @click.stop="$emit('toggle-drawer')" />
    <NuxtLink to="/">
      <v-toolbar-title class="ml-1 subtitle-1 text-header">Dashboard</v-toolbar-title>
    </NuxtLink>
    <NuxtLink to="/#">
      <v-toolbar-title class="ml-5 subtitle-1 text-header">Users</v-toolbar-title>
    </NuxtLink>
    <NuxtLink to="/#">
      <v-toolbar-title class="ml-5 subtitle-1 text-header">Settings</v-toolbar-title>
    </NuxtLink>
    <v-spacer />
    <NuxtLink to="/#">
      <v-icon class="text-header" size="20" to='#'>mdi-bell-outline</v-icon>
    </NuxtLink>
    <NuxtLink to="/#">
      <v-icon class="text-header ml-5" size="20">mdi-format-list-bulleted</v-icon>
    </NuxtLink>
    <NuxtLink to="/#">
      <v-icon class="text-header ml-5" size="20">mdi-email-open-outline</v-icon>
    </NuxtLink>
    <NuxtLink to="/#">
      <v-avatar size="30" class="mx-5">
        <img src="/Nain-2.png">
      </v-avatar>
    </NuxtLink>
    <template v-slot:extension>
      <v-breadcrumbs :items="items">
        <template v-slot:item="{ item }">
          <v-breadcrumbs-item :href="item.href" :disabled="item.disabled">{{ item.text }}
          </v-breadcrumbs-item>
        </template>
      </v-breadcrumbs>
    </template>
  </v-app-bar>
</template>

<script>
  export default {
    data() {
      return {
        drawer: false,
        clipped: false,
        right: true,
        rightDrawer: false,
        items: [{
            text: 'Home',
            disabled: false,
            href: '/',
          },
          {
            text: 'Dashboard',
            disabled: false,
            href: '',
          },
        ],
      }
    }

  }

</script>

<style>
  .text-header {
    color: #2C384AAE;
  }

  .v-toolbar__extension {
    border-top: solid 1px #B1B7C1;
    border-bottom: solid 1px #B1B7C1;
    width: 100%;
    display: flex;
    align-items: center;
    padding: 4px;
  }

</style>
