<script setup>
import { ref, computed } from 'vue'

const broj1 = ref(0)
const broj2 = ref(0)
const operacija = ref('')

const sve_operacije = ['zbrajanje', 'oduzimanje', 'mnozenje', 'dijeljenje']

const provjeraOperacija = computed(() => {
  return sve_operacije.includes(operacija.value)
})
</script>

<template>
  <input type="number" v-model.number="broj1" placeholder="Broj 1">
  <input type="number" v-model.number="broj2" placeholder="Broj 2">
  <input type="text" v-model="operacija" placeholder="Operacija ">

  <div v-if="!provjeraOperacija" class="error">
    Nepoznata operacija! 
  </div>
  <div v-else class="result">
    <span v-if="operacija === 'zbrajanje'">{{ broj1 + broj2 }}</span>
    <span v-else-if="operacija === 'oduzimanje'">{{ broj1 - broj2 }}</span>
    <span v-else-if="operacija === 'mnozenje'">{{ broj1 * broj2 }}</span>
    <span v-else-if="operacija === 'dijeljenje'">{{ broj2 !== 0 ? broj1 / broj2 : 'dijeljenje s 0 nije moguce' }}</span>
    <span v-else-if="operacija === 'dijeljenje' && broj2 === 0" class="error">
        Dijeljenje s 0 nije moguce
    </span>
    <span v-else>0</span>
  </div>
</template>


// Razlika između obične funkcije i computed funkcije , jeste da se computed funkcija ažurira automatski ako dođe do neke promjene, u ovom slucaju kod 'operacija'
