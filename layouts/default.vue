<template>
  <v-app>
    <v-main>
      <v-toolbar color="indigo" dark>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
        <v-toolbar-title>Learning Nuxt</v-toolbar-title>

        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn text class="link">
            <n-link color="success" to="/weather-app">Weather APP</n-link>
          </v-btn>
        </v-toolbar-items>
      </v-toolbar>
      <nuxt />
    </v-main>
  </v-app>
</template>

<style>
.link{
  background-color: white;
}
a{
  text-decoration: none;
  
}
</style>


