<template>
  <v-container class="home">
    <v-row>
      <v-card v-for="todo in todos" :key="todo.id" max-width="344" class="mx-auto mb-6" raised>
        <v-list-item>
          <v-list-item-avatar color="grey">
            <v-img v-bind:src="todo.thumbnailUrl" height="194"></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="headline">{{todo.title}}</v-list-item-title>
            <v-list-item-subtitle>by abdelwahd</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-img v-bind:src="todo.thumbnailUrl" height="194"></v-img>

        <v-card-text>{{todo.url}}</v-card-text>

        <v-card-actions>
          <v-btn text color="blue accent-4">Read More</v-btn>
          <v-spacer></v-spacer>
          <div v-if="like">{{like}}</div>
          <v-btn icon>
            <v-icon>mdi-thumb-up</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-share-variant</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-row>
    <infinite-loading style="width:10%;margin:auto" @infinite="infiniteHandler">
      <div slot="spinner">
        <v-progress-circular indeterminate color="primary"></v-progress-circular>
      </div>
      <div slot="no-more">No more data :)</div>
      <div slot="no-results">No data</div>
    </infinite-loading>
  </v-container>
</template>


<script>
import InfiniteLoading from "vue-infinite-loading";
import axios from "axios";

//const api = "https://jsonplaceholder.typicode.com/photos?_page=" + this.page;

export default {
  components: {
    InfiniteLoading
  },
  data() {
    return {
      page: 498,
      like: 0,
      todos: []
    };
  },
  methods: {
    infiniteHandler($state) {
      axios
        .get("https://jsonplaceholder.typicode.com/photos?_page=" + this.page, {
          params: {
            page: this.page
          }
        })
        .then(({ data }) => {
          if (data.length) {
            this.page += 1;
            this.todos.push(...data);
            $state.loaded();
          } else {
            $state.complete();
          }
        });
    }
  }
};
</script>