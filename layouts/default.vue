<template>
  <v-app>
    <header>
      <v-app-bar
        absolute
        color="black"
        elevate-on-scroll
        app
      >
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
        <v-toolbar-title>hazuma365</v-toolbar-title>
      </v-app-bar>
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
      fixed: false
    }
  }
}
</script>
