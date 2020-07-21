<template>
  <v-app>
    <Header></Header>

    <v-content class="grey lighten-2">
      <router-view></router-view>
    </v-content>

    <Footer></Footer>
  </v-app>
</template>

<script>
import Header from "./views/partials/header";
import Footer from "./views/partials/footer";

export default {
  name: "App",

  components: {
    Header,
    Footer
  },

  data: () => ({
    //
  })
};
</script>
