<script>
import axios from "axios";
import ActorList from "./components/ActorList.vue";
import AppBuffering from "./components/AppBuffering.vue";
import { store } from "./store";
export default{
  components: {
    ActorList,
    AppBuffering,
},
  data(){
    return{
      store
    }
  },
  created(){
    this.store.loading = true;
    axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
      this.store.characters = resp.data
      this.store.loading = false;
    })
  }
}
</script>

<template>
<section>
  <div class="logo">
    <img src="./assets/Breaking_Bad_logo.svg.png" alt="">
    <h1>Breaking Bad Api</h1>
  </div>

    <div class="container">
      <div class="character-found">Found 62 characters</div>
      <AppBuffering v-if="store.loading" />
      <ActorList v-else />
    </div>

</section>

</template>

<style lang="scss">
@use "./components/style/general.scss" as *;
@use "./components/style/partials/variables" as*;

section{
.logo{
display: flex;
align-items: center;
img{
  height: 100px;
}
  h1{
    color: $primary-font-color;
  }
}
  .container{
    background-color: $primary-font-color;
    padding-top: .5rem;
  
    .character-found{
      width: 95%;
      margin: 1.5rem auto;
      background-color: $bg-header-color;
      padding: 1rem 0.5rem;
      color: $primary-font-color;
      font-weight: 600;
    }
  }
}

</style>