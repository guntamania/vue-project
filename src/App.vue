<template>
  <div id="app">
    <v-ons-toolbar>
      <div class="left">
        <v-ons-toolbar-button @click="openSide = !openSide">
          <v-ons-icon icon="ion-navicon, material:md-menu"></v-ons-icon>
        </v-ons-toolbar-button>
      </div>
      <div class="center">vue-project</div>
    </v-ons-toolbar>
    <v-ons-splitter class="content">
      <v-ons-splitter-side
        swipeable width="150px" collapse="" side="left"
        :open.sync="openSide">
        <v-ons-page>
          <v-ons-list>
            <v-ons-list-item v-for="page in pages"
              tappable modifier="chevron"
              @click="openSide = false; $router.push(page.path)">
              {{page.label}}
            </v-ons-list-item>
          </v-ons-list>
        </v-ons-page>
      </v-ons-splitter-side>

      <v-ons-splitter-content>
        <router-view />
      </v-ons-splitter-content>
    </v-ons-splitter>
  </div>
</template>

<script>
import Router from './router'
export default {
  name: 'App',
  data: () => {
    return({
      openSide: false,
      pages: [
        {label: "Top", path: "/"},
        {label: "page1", path: "/page1"}
       ]
    });
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.content {
  margin-top: 58px;
}
</style>
