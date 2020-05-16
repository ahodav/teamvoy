<template>
  <div class="home">
      <div>
        <h1>Pokedex</h1>
      </div>
      <div class="content">
        <List @infoPokemon="toInfoComponent"/>
        <Info :pokemonInfo="info"/>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import List from '@/components/List.vue'
import Info from '@/components/Info.vue'

export default {
  name: 'Home',
  components: {
    List,
    Info
  },
  data () {
    return {
      info: {}
    }
  },
  methods: {
    toInfoComponent (info) {
      this.info = info
    }
  }
}
</script>

<style scoped>
  .content {
    display: flex;
  }
</style>
