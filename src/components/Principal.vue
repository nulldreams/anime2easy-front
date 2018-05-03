<template>
  <div class="principal">
    <select id="animes">
      <option :value="anime.id" v-for="anime in animes" :key="anime.id">{{ anime.nome }}</option>
    </select>
    <a href="#" v-on:click="searchEP()">AAAAAAAAAAAAAAAAA</a>
    <!-- {{episodio}} -->
    <video v-if="episodio.video" controls>
      <source :src="episodio.video" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
</template>

<script>
import api from 'anime2easy'

export default {
  name: 'HelloWorld',
  data () {
    return {
      animes: [],
      episodio: {}
    }
  },
  methods: {
    searchEP: async function () {
      let e = document.getElementById('animes')
      let id = e.options[e.selectedIndex].value

      // let api = require('../assets/anime-api')
      this.episodio = await api.episodio.video(id, 1)
    }
  },
  created () {
    this.animes = require('../assets/animes')
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.principal {
  display: flex;
  flex-direction: column;

  width: 50%;
  margin: 0 auto;
}
</style>
