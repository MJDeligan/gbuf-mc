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
        <span v-if="$vuetify.breakpoint.name != 'xs'" class="align-self-center">Credit for questions to
          <a
            class="white--text"
          href="https://github.com/stiefel40k/PythonMCTester">stiefel40k and bgeVam</a>
        </span>
      </v-container>
    
    </v-app-bar>

    <v-main :class="isdark ? 'main-dark' : ''">
      <HelloWorld :isdark="isdark"/>
      <v-sheet :class="['justify-center d-flex mb-8', isdark? 'main-dark' : '']">
        <v-btn
          @click="dialog = !dialog"
          icon
          class="align-self-center mr-4"
          :color="isdark ? 'white' : 'grey'"
        >
          <v-icon large>mdi-information</v-icon>
        </v-btn>
        <v-switch
          :append-icon="isdark ? 'mdi-brightness-5':'mdi-brightness-3'"
          color="deep-orange"
          v-model="isdark"
        >
        </v-switch>
      </v-sheet>
      <v-dialog
        v-model="dialog"
        max-width="75%"
      >
      <v-card>
        <v-card-title class="mb-4">Welcome</v-card-title>
        <v-card-text class="red--text">Answers might not be correct! This is not a substitute for actually studying for the test!</v-card-text>
        <v-card-text class="primary--text">If you find any errors let me know:</v-card-text>
        <v-card-text class="primary--text">
          <v-icon color="primary">mdi-email</v-icon>
          <span>marco.razor@hotmail.com</span>
        </v-card-text>
        <v-list>
          <v-list-item class="mb-2">The number next to the question indicates the number of correct answers</v-list-item>
          <v-list-item class="mb-2">Press the Validate-Button to check your answers</v-list-item>
          <v-list-item class="mb-2">Press the Next-Button for the next Question</v-list-item>
          <v-list-item class="mb-2">Night mode can be toggled with the switch below the question container</v-list-item>
        </v-list>
      </v-card>
      </v-dialog>
      <span v-if="$vuetify.breakpoint.name == 'xs'" :class="['align-self-center ml-4', isdark ? 'white--text' : '']">Credit for questions to
          <a
            href="https://github.com/stiefel40k/PythonMCTester"
          >stiefel40k and bgeVam</a>
        </span>
    </v-main>
  </v-app>
</template>
<style scoped>
.main-dark {
  background-color: rgb(20, 20, 20);
}
.container {
  max-width: 1200px;
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
    isdark: false,
    dialog: false
  }),
};
</script>
