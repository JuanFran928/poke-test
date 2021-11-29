<template>
<div class="container">
  <h1>{{name}}</h1>
  <img :src="image" style="width:90px" />
</div>
</template>
<script>
export default {
  name: "Pokemon",
  mounted() {
    this.getPokemonData();
  },
  data() {
    return {
        id: 1,
        name: '',
        image: '',
    };
  },
  watch:{
    $route(to){
    this.id = Number(to.params.id);
    this.getPokemonData();
}},
  methods: {
    getPokemonData() {
      
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.id}`)
        .then(response => response.json())
        .then(data => {
            this.name = data.name;
            this.image = data.sprites.front_default;
        });

    }
  }
}
</script>
<style>
.container{
  width: '500px';
  height: '600px';
  background-image: url('../assets/pokedex1.png');
  background-repeat: no-repeat;
  background-position: center;
  background-size: 250px 110px;
}

</style>