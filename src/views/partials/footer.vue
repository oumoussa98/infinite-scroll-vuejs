<template>
  <v-footer
    color="grey darken-2"
    padless
  >
    <v-row
      justify="center"
      no-gutters
    >
      <v-btn
        v-for="link in links"
        :key="link"
        color="white"
        text
        rounded
        class="my-2"
      >
        {{ link }}
      </v-btn>
      <v-col
        class="grey darken-1 py-4 text-center white--text"
        cols="12"
      >
       Follow me on
    <a class="mr-2 ml-2" href="http://www.twitter.com/oumoussa98/" target="_blanck" >
       <v-icon>mdi-twitter</v-icon></a>
    <a class="mr-2" href="http://www.facebook.com/oumoussa98/" target="_blanck">
       <v-icon>mdi-facebook</v-icon></a>
    <a class="mr-2" href="http://www.instagram.com/oumoussa98/" target="_blanck">
       <v-icon>mdi-instagram</v-icon></a>
       <a class="mr-2" href="http://www.github.com/oumoussa98/" target="_blanck">
       <v-icon>mdi-github</v-icon></a>
      </v-col>
    </v-row>
  </v-footer>
</template>

<script>
  export default {
    data: () => ({
      links: [
        'Home',
        'About Us',
        'Team',
        'Services',
        'Blog',
        'Contact Us',
      ],
    }),
  }
</script>
<style scoped>
    a {
        text-decoration: none;
    }
</style>