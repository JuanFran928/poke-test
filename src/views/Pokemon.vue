<template>
<div>{{name}}</div>
</template>
<script>
export default {
  name: "Pokemon",
  mounted() {
    this.getPokemonData();
  },
  data() {
    return {
      id: 0,
        name: '',
    };
  },
  watch:{
      $route(to){

     this.id = Number(to.params.id);
     this.getPokemonData();
}},
  methods: {
    getPokemonData() {
      console.log(this.id);
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.id}`)
        .then(response => response.json())
        .then(data => {
            this.name = data.name;
            console.log(data)
        });

    }
  }
}
</script>
<style>
</style>