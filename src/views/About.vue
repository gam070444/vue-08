<template>
  <div class="container">
    <img />
    <img
      :src="animeList.image_url"
      alt="Girl in a jacket"
      width="500"
      height="600"
    />

    <b-card>
      <b-card-title></b-card-title>
      <b-card-text class="small text-muted">Last updated 3 mins ago</b-card-text>
      <b-card-title>{{ animeList.title }} </b-card-title>
      <b-card-text> Type : {{ animeList.type }} </b-card-text>
      <b-card-text> Synopsis : {{ animeList.synopsis }} </b-card-text>
      <b-card-text class="big text-muted">Last updated 3 mins ago</b-card-text>
    </b-card>

  </div>
</template>
<script>
import axios from "axios";
export default {
  //  https://api.jikan.moe/v3/anime/20
  data() {
    return {
      animeList: null,
      url: `https://api.jikan.moe/v3/anime/${this.$route.params.id}`,
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