<script setup>
import { ref, computed } from 'vue'

const sportasi = ref([
  {
    ime: 'Ana',
    disciplina: 'atletika',
    godine: 30,
    natjecanja: ['Svjetsko prvenstvo', 'Europsko prvenstvo', 'Olimpijske igre']
  },
  {
    ime: 'Ivan',
    disciplina: 'plivanje',
    godine: 25,
    natjecanja: ['Olimpijske igre', 'Svjetsko prvenstvo']
  },
  {
    ime: 'Marko',
    disciplina: 'odbojka',
    godine: 22,
    natjecanja: ['Europsko prvenstvo']
  }
])


const novo_natjecanje = ref('')

const dodaj_natjecanje = (sportasIndex) => {
  if (novo_natjecanje.value !== '') {
    sportasi.value[sportasIndex].natjecanja.push(novo_natjecanje.value)
    novo_natjecanje.value = ''
  }
}

const ukloni_natjecanje = (sportasIndex, natjecanjeIndex) => {
  sportasi.value[sportasIndex].natjecanja.splice(natjecanjeIndex, 1)
}

const sortiraniSportasi = computed(() => {
  return [...sportasi.value].sort((a, b) => b.natjecanja.length - a.natjecanja.length)
})

</script>

<template>
    <div>
      <input v-model="novo_natjecanje" placeholder="Dodaj natjecanje" />
  
      <div v-for="(sportas, index) in sortiraniSportasi" :key="index">
        <p>
          <span v-if="index === 0">🥇</span>
          <span v-else-if="index === 1">🥈</span>
          <span v-else-if="index === 2">🥉</span>

          <span>Ime:</span> {{ sportas.ime }}<br>
          <span>Godine:</span> {{ sportas.godine }}<br>
          <span>Disciplina:</span> {{ sportas.disciplina }}<br>

          <span>Natjecanja:</span><button @click="dodaj_natjecanje(index)">+</button>
        </p>
        <ul >
        <li v-for="(natjecanje, natjecanjeIndex) in sportas.natjecanja" :key="natjecanje" >
          <button @click="ukloni_natjecanje(index, natjecanjeIndex)" >-</button>
          {{ natjecanje }}
        </li>
      </ul>
      </div>
    </div>
</template>

<style scoped>
.list-enter-active,
.list-leave-active {
 transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
 opacity: 0;
 transform: translateX(30px);
}
</style>

  