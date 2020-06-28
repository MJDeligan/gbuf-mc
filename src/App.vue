<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-container class="d-flex align-center">
        <v-toolbar-title>MC-Tester</v-toolbar-title>
        <v-spacer class="ml-auto"></v-spacer>
        <span class="align-self-center">Credits to
          <a
            class="white--text"
          href="https://github.com/stiefel40k/PythonMCTester">stiefel40k and bgeVam</a>
        </span>
      </v-container>
    
    </v-app-bar>

    <v-main :class="isdark ? 'main-dark' : ''">
      <HelloWorld :isdark="isdark"/>
      <v-sheet :class="['justify-center d-flex', isdark? 'main-dark' : '']">
        <v-switch
          :append-icon="isdark ? 'mdi-brightness-5':'mdi-brightness-3'"
          color="deep-orange"
          v-model="isdark"
        >
        </v-switch>
      </v-sheet>
    </v-main>
  </v-app>
</template>
<style scoped>
.main-dark {
  background-color: rgb(20, 20, 20);
}


</style>
<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    isdark: false
  }),
};
</script>
