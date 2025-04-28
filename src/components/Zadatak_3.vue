<script setup>

import Slika from '@/components/Slika.vue' 
import { ref } from 'vue'

const galerija = [    
    {
        slikar: "Pablo Picasso",
        godina: 1903,
        naslov: "The Old Guitarist",
        slika: "/src/assets/slike/The Old Guitarist.png"
    },
    {
        slikar: "Vincent van Gogh",
        godina: 1886,
        naslov: "Le Moulin de Blute-Fin",
        slika: "/src/assets/slike/Le Moulin de Blute-Fin.png"
    },
    {
        slikar: "Hokusai",
        godina: 1890,
        naslov: "Courtesan Asleep",
        slika: "/src/assets/slike/Courtesan Asleep.png"
    },
];
const povecana_slika = ref('')
  
function povecaj_sliku(slika) {
    povecana_slika.value = slika
}
</script>

<template>
    <div style="border: 2px solid lightgray; border-radius: 6px;">
      <div style="display: flex; gap: 20px; flex-wrap: wrap;">
        <slika
          v-for="(slika, index) in galerija"
          :key="index"
          :slikar="slika.slikar"
          :godina="slika.godina"
          :naslov="slika.naslov"
          :slika="slika.slika"
          @povecaj="povecaj_sliku"
        />
      </div>
      <div v-if="povecana_slika" style="margin-top: 15px;">
        <img :src="povecana_slika" alt="Uvećana slika" style="max-width: 100%; height: auto;" />
      </div>
    </div>
</template>
  
  
  
  
