<script setup>
   const pokemon = defineProps(['name','xp', 'height', 'image' ,'loading'])
</script>

<template>
  <div 
     class="card p-2 card-pokemon-selected text-body-secondary"
    :class="loading ? '' : 'animate__animated animate__flipInX'"
  >
  <!-- <h1 class="animate__animated animate__bounce" >POKEMONS SAIL</h1>      -->
    <img
    v-if="pokemon.name"
      :src="pokemon.image"
      class="card-img-top pt-2"
      alt="pokemon.name"
    />

    <img
      v-else
      src="../assets/egg_pokemon.svg"
      height="250"
      class="card-img-top pt-2"
      alt="????"
    />
    <div class="card-body">
      <h5 class="card-title text-center">{{ pokemon.name || '????' }}</h5>
      <hr />
        <div class="d-none d-md-block">
              <div class="row">
        <section class="col">
          <strong>XP:</strong>
          <span>{{ pokemon.xp }}</span>
        </section>
        <section class="col">
          <strong>Altura:</strong>
          <span>{{ pokemon.height }}</span>
        </section>
      </div>
        </div>
                
    </div>
  </div>
</template>

<style scoped>

    .card-pokemon-selected{
            background: #e4d1a1;
             background: radial-gradient(circle, rgba(199, 192, 94, 0.8) 35%, rgb(162, 0, 255) 100%);
             min-height: 75vh;
    }

     .card-pokemon-selected img{
            height: 250px;
    }

    @media (max-width: 768px) {
        .card-pokemon-selected{
            width: 45%;
             min-height: 40vh;
             margin: 0 auto 10px auto;
         }

        .card-pokemon-selected img{
            height: 100px;
        
        }
   


    }

</style>
