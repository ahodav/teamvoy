<template>
  <div class="card" @click="checkInfo(pokemon)">
    <div>
      <img class="pokemon-img" :src="pokemon.sprites.front_default" alt="">
    </div>
    <p class="name"><strong>{{pokemon.name}}</strong></p>
    <div class="ability">
        <span v-for="type in pokemon.types" :class="type.type.name" :key="type.toString() + type.type.name">
          {{type.type.name}}
        </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    pokemon: Object
  },
  methods: {
    checkInfo (item) {
      this.$emit('singlePokemon', item)
    }
  }
}
</script>

<style>

.card {
  margin: 5px;
  border: 1px solid black;
  max-width: 300px;
  max-height: 400px;
  min-width: 200px;
  min-height: 200px;
  border-radius: 8px;
}

.name {
  text-transform: capitalize;
}

.pokemon-img {
  max-width: 300px;
  max-height: 100px;
  width: 115px;
  height: auto;
}

.fire {
  border: 1px solid yellow;
  background: yellow;
  border-radius: 4px;
  padding: 4px;
}

.water {
  border: 1px solid lightblue;
  background: lightblue;
  border-radius: 4px;
  padding: 4px;
}

.bug {
  border: 1px solid brown;
  background: brown;
  border-radius: 4px;
  padding: 4px;
}

.poison {
  border: 1px solid green;
  background: green;
  border-radius: 4px;
  padding: 4px;
}

.grass {
  border: 1px solid lightgreen;
  background: lightgreen;
  border-radius: 4px;
  padding: 4px;
}

.flying  {
  border: 1px solid lightsteelblue;
  background: lightsteelblue;
  border-radius: 4px;
  padding: 4px;
}

.normal  {
  color: white;
  border: 1px solid purple;
  background: purple;
  border-radius: 4px;
  padding: 4px;
}

.electric  {
  border: 1px solid wheat;
  background: wheat;
  border-radius: 4px;
  padding: 4px;
}

.fairy  {
  border: 1px solid lightgrey;
  background: lightgrey;
  border-radius: 4px;
  padding: 4px;
}

.ground  {
  border: 1px solid lightslategray;
  background: lightslategray;
  border-radius: 4px;
  padding: 4px;
}

</style>
