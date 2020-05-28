<template>
  <v-app>
    <v-app-bar app color="teal" dark>
      <div class="title">
        Formulate Playground
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-content>
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
