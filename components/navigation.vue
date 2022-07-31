<template>
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" :clipped="clipped" fixed app class="primary ">
      <!-- titre -->
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="white--text text-h5 text-center">{{ title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-list v-for="(category,i) in nav" :key='i'  class="secondary pa-0">

        <!-- gestion des categories et du dashboard -->

        <v-list-item v-if="category.type=='item'" class="greyTextNavBar--text" :to="category.to">
          <v-list-item-icon>
            <v-icon class="greyTextNavBar--text">{{ category.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="category.title" />
          </v-list-item-content>
        </v-list-item>

        <v-list-item v-if="category.type=='category'" class="greyTextNavBar--text">
          <v-list-item-content>
            <v-list-item-title class="subtitle-2 text-uppercase" v-text="category.title" />
          </v-list-item-content>
        </v-list-item>

        <!-- gestion des pages -->

        <v-list v-for="(children,i) in category.children" :key="i" class="pa-0">
          <v-list-item v-if="children.type=='item'" :to="children.to" class="greyTextNavBar--text ">
            <v-list-item-icon>
              <v-icon class="greyTextNavBar--text">{{ children.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="children.title" />
            </v-list-item-content>
          </v-list-item>
          
          <v-expansion-panels tile flat>
          <v-expansion-panel accordion v-if="children.type=='collapse'" :to="children.to" class="secondary greyTextNavBar--text ">
            <v-expansion-panel-header class="py-0 px-4 ">
              <v-list-item-icon class=" noflex">
                <v-icon class="greyTextNavBar--text">{{ children.icon }}</v-icon>
              </v-list-item-icon>
              <v-list-item-content class="pa-0">
                <v-list-item-title v-text="children.title" />
              </v-list-item-content>
            </v-expansion-panel-header>
            <v-expansion-panel-content color="primary">
              <v-list >
              <v-list-item v-for="(children,i) in children.children" :key="i" :to="children.to">
                <v-list-item-content class="pl-13 py-0 greyTextNavBar--text">
                  <v-list-item-title v-text="children.title" />
                </v-list-item-content>
              </v-list-item>
              </v-list>
            </v-expansion-panel-content>
          </v-expansion-panel>
          </v-expansion-panels>
        </v-list>

      </v-list>

      <v-list class="d-flex justify-end mr-3">
        <v-btn icon @click.stop="miniVariant = !miniVariant">
          <v-icon class="greyTextNavBar--text">mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
        </v-btn>
      </v-list>

    </v-navigation-drawer>
</template>

<script>
  export default {
    name: "navigation",

    data() {
      return {
        drawer: true,
        clipped: false,
        miniVariant: false,
        title: 'CoreUI',
        iconTitle: 'mdi-alpha-c-circle-outline',
        nav: [{
            title: "Dashboard",
            icon: "mdi-view-dashboard-outline",
            to: "/",
            type: "item"
          },
          {
            title: "Theme",
            type: "category",
            children: [{
                title: "Colors",
                icon: "mdi-water-outline",
                to: "/color",
                type: "item"
              },
              {
                title: "Typography",
                icon: "mdi-pencil-outline",
                to: "/#",
                type: "item"
              }
            ]
          },
          {
            title: "Components",
            type: "category",
            children: [{
              title: "Base",
              icon: "mdi-puzzle-outline",
              to: "#",
              type: "collapse",
              children:[{
                title: "Accordion",
                to:"#",
                type:"item"
              },
              {
                title: "Breadcrumbs",
                to:"#",
                type:"item"
              },
              {
                title: "Cards",
                to:"#",
                type:"item"
              },
              ]
            },
            {
              title: "Buttons",
              icon: "mdi-arrow-top-right-bold-outline",
              to: "#",
              type: "collapse",
                children:[{
                title: "Buttons",
                to:"#",
                type:"item"
              },
              {
                title: "Button Groups",
                to:"#",
                type:"item"
              },
              {
                title: "Dropdowns",
                to:"#",
                type:"item"
              },
              ]
            },
            {
              title: "Forms",
              icon: "mdi-format-columns",
              to: "#",
              type: "collapse",
                children:[{
                title: "Form Control",
                to:"#",
                type:"item"
              },
              {
                title: "Select",
                to:"#",
                type:"item"
              },
              {
                title: "Check & Radios",
                to:"#",
                type:"item"
              },
              ]
            },
            {
              title: "Charts",
              icon: "mdi-chart-donut",
              to: "#",
              type: "item"
            },
            {
              title: "Icons",
              icon: "mdi-star-outline",
              to: "#",
              type: "collapse",
                children:[{
                title: "CoreUi Icons",
                to:"#",
                type:"item"
              },
              {
                title: "Brands",
                to:"#",
                type:"item"
              },
              {
                title: "Flags",
                to:"#",
                type:"item"
              },
              ]
            },
            {
              title: "Notifications",
              icon: "mdi-bell-outline",
              to: "#",
              type: "collapse",
                children:[{
                title: "Alerts",
                to:"#",
                type:"item"
              },
              {
                title: "Badges",
                to:"#",
                type:"item"
              },
              {
                title: "Modals",
                to:"#",
                type:"item"
              },
              ]
            },
            {
              title: "Widgets",
              icon: "mdi-widgets-outline",
              to: "#",
              type: "item"
            },]
          },{
            title: "Extras",
            type: "category",
            children: [{
              title: "Pages",
              icon: "mdi-star-outline",
              to: "#",
              type: "collapse",
              children:[{
                title: "Login",
                to:"#",
                type:"item"
              },
              {
                title: "Register",
                to:"#",
                type:"item"
              },
              {
                title: "Error 404",
                to:"#",
                type:"item"
              },
              ]
            }],
          }
        ]
      }
    }

  }

</script>

<style>
  .mdi-chevron-down{
    color: #B1B7C1 !important;
  }
  .v-expansion-panel-content__wrap{
    padding: 0;
  }
  .noflex{
    flex: unset !important;
  }
</style>
