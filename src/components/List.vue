<template>
  <div>
    <div class="list-content">
      <div v-for="(item, index) in results" :key="index">
        <Card @singlePokemon="toParent" :pokemon="item"/>
      </div>
    </div>
    <div class="list-content">
      <button
        class="loadMore"
       @click="loadinfo(nextLoad)"
        >
        Load more
      </button>
    </div>
  </div>
</template>

<script>

import Card from './Card.vue'
import axios from 'axios'

export default {
  components: {
    Card
  },
  data () {
    return {
      nextLoad: null,
      results: [],
      baseUrl: 'https://pokeapi.co/api/v2/pokemon?limit=12'
    }
  },
  methods: {
    toParent (item) {
      this.$emit('infoPokemon', item)
    },
    loadinfo (url) {
      axios
        .get(url)
        .then(res => {
          this.nextLoad = res.data.next
          const results = res.data.results
          results.forEach(element =>
            axios
              .get(element.url)
              .then(response => {
                const data = response.data
                this.results.push(data)
              })
          )
        })
    }
  },
  mounted () {
    this.loadinfo(this.baseUrl)
  }

}
</script>

<style scoped>
  .list-content {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    max-width: calc(100% - 200px);
  }

  .loadMore {
    color: white;
    background: blue;
    height: 32px;
    width: 120px;
    border: 0;
    border-radius: 4px;
  }
</style>
