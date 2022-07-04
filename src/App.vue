<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="@/assets/Logo-Borg.png"
          transition="scale-transition"
          width="200"
        />
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main>
      <BorgInfo/>
    </v-main>
    <v-footer
    color="primary"
    height="70"
    >proudly presented by Gymnasium Bad Leonfelden</v-footer>
  </v-app>
</template>

<script>
import BorgInfo from './components/BorgInfo';

export default {
  name: 'App',

  components: {
    BorgInfo,
  },

  data: () => ({
    //
  }),
};
</script>
