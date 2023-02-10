<script setup>
import { ref, computed } from 'vue';

const name = "Vue 3"

const counter = ref(0)

const increment = () => {
  counter.value++
}

const decrement = () => {
  counter.value--
}

const reset = () => {
  counter.value = 0
}

const arrayCounter = ref([])

const addNumber = () => {
  arrayCounter.value.push(counter.value)
  console.log(counter.value)
}

const blockNumber = computed(() => {
  const number = arrayCounter.value.find((num) => num === counter.value)
  return number || number === 0
})

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero'
  }

  if (counter.value > 0) {
    return 'positive'
  }

  if (counter.value < 0) {
    return 'negative'
  }

})



</script>

<template>

  <div class="container text-center mt-3">
    <h1>Hola {{ name }}</h1>

    <h2 :class="classCounter">{{ counter }}</h2>

    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar contador</button>
      <button @click="decrement" class="btn btn-danger">Diminuir contador</button>
      <button @click="reset" class="btn btn-secondary">Resetear contador</button>
      <button @click="addNumber" :disabled="blockNumber" class="btn btn-primary">Agregar</button>
    </div>

    <h2 class="mt-4">Favoritos</h2>
    <ul class="list-group  mt-4">
      <li class="list-group-item" v-for="(number, index) in arrayCounter" :key="index">{{ number }}</li>
    </ul>
  </div>

</template>

<style>
.negative {
  color: red;
}

.positive {
  color: green;
}

.zero {
  color: white;
}
</style>
