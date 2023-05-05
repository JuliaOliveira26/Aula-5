<script setup>
  import { ref } from 'vue'

  const novoItem = ref('')
  const listaCompras = ref([ 'arroz', 'batata', 'feijão' ])
  
  function adicionar (index){
    listaCompras.value.push(index, novoItem.value)
    novoItem.value = ''
  }
</script>
<template>
  <input type="text" v-model="novoItem">
  <button @click="adicionar">Adicionar</button>
  <ul>
    <li @v-for="(item,index) in listaCompras">{{ listaCompras }}</li>
  </ul>
</template>
