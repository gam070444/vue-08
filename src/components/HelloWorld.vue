<template>
  <div class="hello">
    <router-link :to="`/about/${this.id}`">
  <b-card
    :title="name"
    :img-src="img"
    img-alt="Image"
    img-top
    tag="article"
    style="width: 25rem;height:40rem"
    img-height="500"
    class="mb-4 mr-4 offset-md-1 col-12"
  >
  </b-card>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    id:Number,
    name:String,
    img:String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
