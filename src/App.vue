<script>
import axios from "axios";
import { store } from "./store";
import AppSearch from "./components/AppSearch.vue";
import AppMain from "./components/AppMain.vue";
export default {
  components: { AppSearch, AppMain },
    data() {
    return {
      store,
    };
  },
  created() {
    this.getResult();
  },
  methods: {
    getResult() {
      axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: this.store.apiKey,
          query: this.store.searchQuery,
        },
      })
      .then((resp) => {
        console.log(resp);
        this.store.moviesArray = resp.data.results;   
      });
    }
  }

};
</script>

<template>
  <AppSearch @change="getResult" />
  <AppMain />
</template>

<style lang="scss"></style>