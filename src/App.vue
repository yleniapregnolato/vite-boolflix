<script>
import axios from "axios";
import { store } from "./store";
export default {
  data() {
    return {
      store,
    };
  },
  created() {
   axios
   .get("https://api.themoviedb.org/3/search/movie", {
    params: {
      api_key: this.store.apiKey,
      query:"ciao",
    },
   })
   .then((resp) => {
    console.log(resp);
   })
  }
}
</script>