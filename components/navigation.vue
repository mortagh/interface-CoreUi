<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" :clipped="clipped" fixed app class="primary ">
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="white--text text-h6">
                    <p> {{ title }} </p>
                </v-list-item-title>
            </v-list-item-content>
        </v-list-item>
      <v-list>
        <v-list-item v-for="(item, i) in nav" :key="i" :to="item.to" router exact
            class="secondary greyTextNavBar--text">
            <v-list-item-icon v-if="item.icon">
                <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
                <v-list-item-title v-text="item.title" />
            </v-list-item-content>

            <v-list-item v-for="(category,i) in item.categories" :key="i">
                <v-list-item-content>
                    <v-list-item-title v-text="category.title" />
                </v-list-item-content>

                <!-- <v-list-item v-for="(children,i) in category.children" :key="i" :to="children.to">
                    <v-list-item-action>
                        <v-icon>{{ children.icon }}</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                        <v-list-item-title v-text="children.title" />
                    </v-list-item-content>
                </v-list-item> -->
            </v-list-item>
        </v-list-item>
        <v-btn icon @click.stop="miniVariant = !miniVariant">
          <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
        </v-btn>
      </v-list>
    </v-navigation-drawer>
  </v-app>
</template>

<script>
  export default {
    name: "navigation",
    data() {
      return {
        drawer: false,
        clipped: false,
        miniVariant: false,
        title: 'CoreUI',
        iconTitle: 'mdi-alpha-c-circle-outline',
        nav: [{
            title: 'Dashboard',
            icon: 'mdi-view-dashboard-outline',
            to: '/',
          },
          {
            categories: [{
                title: 'theme',
                children: [{
                    title: 'Color',
                    icon: 'mdi-water-outline',
                    to: '/inspire',
                  },
                  {
                    title: 'Typography',
                    icon: 'mdi-pencil-outline',
                    to: '/#',
                  }
                ],
              },
              {
                title: 'Components',
                children: [{
                  title: 'Base',
                  icon: 'mdi-puzzle'
                }]
              }
            ],
          }
        ],
      }
    }

  }

</script>

<style>

</style>
