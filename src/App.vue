<template>
  <div id="app">
    <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <router-link to="/"><h2 class="b">Anime</h2></router-link>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input
                size="sm"
                class="mr-sm-2"
                placeholder="Search"
                v-model="sh"
              ></b-form-input>
              <b-button size="sm" class="my-2 my-sm-0" type="submit" @click="search()"
                >Search</b-button
              >
            </b-nav-form>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <div id="nav">
      
    </div>
    <router-view />
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      sh: "",
      mangaList: "",
      url: "https://api.jikan.moe/v3/producer/1/3",
    };
  },
  methods: {
    search() {
      const router = this.$router;
      for (let i = 0; i <= this.mangaList.anime.length; i++) {
        if (this.sh == this.mangaList.anime[i].title) {
          alert(this.mangaList.anime[i].title);
          router.push({
            path: `/about/${this.mangaList.anime[i].mal_id}`,
          });
          break;
        } else if (99 == i) {
          alert("Not listed!!!");
          router.push({
            path: `/`,
          });
        }
      }
    },
  },
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.mangaList = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>















<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.b{
  color: rgb(255, 255, 255);
}
</style>
