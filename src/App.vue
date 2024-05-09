<script>
import axios from "axios";
import { store } from "./store";
import AppSearch from "./components/AppSearch.vue";
export default {
  components: { AppSearch },
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
        this.store.moviesArray = resp.data.results;
        console.log(resp);
      });
    }
  }

};
</script>

<template>
  <AppSearch @filter="getResult" />
</template>

<style lang="scss"></style>