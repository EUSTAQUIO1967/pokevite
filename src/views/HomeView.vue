<script setup>


import { onMounted, reactive, ref, computed } from "vue";
import ListPokemons from "@/components/ListPokemons.vue";

import CardPokemonSelected from "@/components/CardPokemonSelected.vue";

let pokemons = reactive(ref());

let searchPokemonField = ref('');

let pokemonSelected = reactive(ref());

let loading = ref(false);

let urlBaseSvg =
  "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/";

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
    .then((res) => res.json())
    .then((res) => {
      pokemons.value = res.results;
    });
});

const pokemonsFiltered = computed(() => {
  if (pokemons.value && searchPokemonField.value) {
    return pokemons.value.filter(pokemon => pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase()))
  }
  return pokemons.value
})  


const selectPokemon = async (pokemon) => {

  loading.value = true

  await fetch(pokemon.url)
    .then(res => res.json())
    .then(res => pokemonSelected.value = res)
    .catch(err => alert(err))
    .finally(() => {
      loading.value = false
    })

  console.log(pokemonSelected.value);
}
</script>

<template>
  <main>
    <div class="container text-secondary">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          <CardPokemonSelected 
            :name="pokemonSelected?.name"
            :xp="pokemonSelected?.base_experience"
            :height="pokemonSelected?.height"
            :image="pokemonSelected?.sprites.other.dream_world.front_default"
            :loading="loading"
          />

          
        </div>
        <div class="col-sm-12 col-md-6 card-list">
          <div class="card">
            <div class="card-body row">
              <!-- input de busca -->
              <div class="mb-3">
                <label hidden for="search-pokemon-field" class="form-label"
                  >Email address</label
                >
                {{ searchPokemoField }}
                <input 
                  type="text"
                  v-model="searchPokemonField"
                  class="form-control"
                  id="search-pokemon-field"
                  placeholder="Pesquisar ... "

                  
                />
              </div>

              <ListPokemons
                v-for="pokemon in pokemonsFiltered"
                :key="pokemon.name"
                :name="pokemon.name"
                :url="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
                @click="selectPokemon(pokemon)"
              >
              </ListPokemons>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.card-list {
  max-height: 75vh;
  overflow-y: auto;
  overflow-x: hidden;
}

@media (max-width:768px) {
  .card-list {
  max-height: 45vh;
  
}
}
</style>