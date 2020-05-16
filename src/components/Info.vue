<template>
  <div class="info">
    <div v-if="pokemonInfo.sprites == undefined">Select hero for detals</div>
    <div v-else>
      <div class="pokemonInfo">
        <img :src="pokemonInfo.sprites.front_default" alt="">
      </div>
      <h1 class="name">{{pokemonInfo.name}}</h1>
      <table border="1" style="margin: 0 auto">
      <tbody>
      <tr>
      <td>Type</td>
      <td><span v-for="(type, index) in pokemonInfo.types" :key="index">{{type.type.name}} </span></td>
      </tr>
      <tr>
      <td>Attack</td>
      <td>{{pokemonInfo.stats[4].base_stat}}</td>
      </tr>
      <tr>
      <td>Defense</td>
      <td>{{pokemonInfo.stats[3].base_stat}}</td>
      </tr>
      <tr>
      <td>HP</td>
      <td>{{pokemonInfo.stats[5].base_stat}}</td>
      </tr>
      <tr>
      <td>SP Attack</td>
      <td>{{pokemonInfo.stats[2].base_stat}}</td>
      </tr>
      <tr>
      <td>SP Defense</td>
      <td>{{pokemonInfo.stats[1].base_stat}}</td>
      </tr>
      <tr>
      <td>Speed</td>
      <td>{{pokemonInfo.stats[0].base_stat}}</td>
      </tr>
      <tr>
      <td>Weight</td>
      <td>{{pokemonInfo.weight}}</td>
      </tr>
      <tr>
      <td>Total moves</td>
      <td>{{pokemonInfo.moves.length}}</td>
      </tr>
      </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pokemonInfo: Object
  },
  data () {
    return {
      totalmoves: 0,
      types: ''
    }
  }
}
</script>

<style>

.info{
  position: fixed;
  top: 70px;
  right: 0;
  margin: 0 auto;
  min-width: 200px;
  max-width: 200px;
}
</style>
