<script setup>
defineProps({
    slikar:String,
    godina:Number,
    naslov:String,
    slika:String,
});

function starost(godina) {
  const trenutnaGodina = new Date().getFullYear()
  return trenutnaGodina - godina

}
</script>
<template>
  <div style="text-align: center;">
    <img 
      :src="slika" 
      alt="slika" 
      height="100" 
      @click="$emit('povecaj', slika)"
    />

    <div>
      <strong>Naslov:</strong>
      <span :class="{ underline: starost() > 136 }">{{ naslov }}</span>
    </div>

    <div><strong>Slikar:</strong> {{ slikar }}</div>
    <div><strong>Starost:</strong> {{ starost(godina) }}</div>

  </div>

</template>

<style>

</style>




