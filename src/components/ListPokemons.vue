<script setup>
const pokemon = defineProps([
    "name", "url"
])
    
</script>

<template>
<div class="col-4 col-md-6 col-lg-3 col-xl-3">
    <div class="card mb-3 p-2 card-list-pokemon text-body-secondary" >
        <p class="text-center">{{ pokemon.name }}</p>
        <img 
        :src="url" 
        :alt="pokemon.name" 
        height="80" 
        />
    </div>
</div>
</template>

<style scoped>

.card-list-pokemon{
    background: #097977;
    background: radial-gradient(circle, rgba(9, 121, 119, 0.48) 35%, rgba(0, 212, 255, 1) 100%);
 cursor: pointer   
}

.card-list-pokemon:hover{
    background: #097977;
    background: radial-gradient(circle, rgba(9, 121, 119, 0.6) 35%, rgba(0, 212, 255, 0.9) 100%);
    transform: rotate(10deg);
    
}

.card-list-pokemon img:hover{
    padding: 0.2rem;
    
}

</style>