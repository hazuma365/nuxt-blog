<template>
  <v-app>
    <header>

      <v-app-bar
        absolute
        elevate-on-scroll
        app
      >
        <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
        <v-toolbar-title>hazuma365</v-toolbar-title>
      </v-app-bar>
      <v-navigation-drawer
                v-model="drawer"
                fixed
                clipped
                temporary
              >
                <v-list-item>
                  <v-list-item-title class="title">
                    {{title}}
                  </v-list-item-title>
                  <v-btn icon @click="drawer = false">
                    <v-icon>mdi-chevron-left</v-icon>
                  </v-btn>
                </v-list-item>
                <v-list>
                  <v-list-item
                    v-for="(item, i) in items"
                    :key="i"
                    :to="item.to"
                    router
                    exact
                  >
                    <v-list-item-action>
                      <v-icon>{{ item.icon }}</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                      <v-list-item-title v-text="item.title" />
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-navigation-drawer>
    </header>
    <!--Main -->
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <!--Footer -->
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      title: 'hazuma365',
      fixed: true,
      drawer: false,
      items: [
        {
          icon: 'mdi-home',
          title: 'HOME',
          to: '/'
        },
        {
          icon: 'mdi-file-document',
          title: 'ARTICLES',
          to: '/'
        },
      ],
    }
  }
}
</script>
