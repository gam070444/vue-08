<template>
  <div class="home">
    <div class="row col-12">
      <HelloWorld
        v-for="(item, index) in animeList.anime"
        :key="index"
        :name="item.title"
        :img="item.image_url"
        :id="item.mal_id"
class="col-3"
      />

    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import HelloWorld from "@/components/HelloWorld.vue";
export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  props: {
    page: Number,
  },
  data() {
    return {
      animeList: null,
      url: "https://api.jikan.moe/v3/producer/1/3",
    };
  },
  mounted() {
    axios
      .get(this.url)
      .then((result) => {
        this.animeList = result.data;
      })
      .catch((err) => {
        console.log(err);
        alert(err);
      });
  },
};
</script>


