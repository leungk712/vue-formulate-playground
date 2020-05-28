<template>
  <v-app>
    <v-app-bar app color="teal" dark>
      <div class="title">
        Kev's VueFormulate Playground
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-content class="blue-grey lighten-1">
      <Form />
    </v-content>
  </v-app>
</template>

<script>
import Form from "./views/Form";

export default {
  name: "App",

  components: { Form },

  data: () => ({
    //
  })
};
</script>
