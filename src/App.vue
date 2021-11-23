<template>
<div class="container text-center">
  <h1>Carrito</h1>
  <hr>
  <carrito/>
  <div class="row">
   <card
     v-for="producto of productos" :key="producto.id"
     :producto="producto"
   />
  </div>
</div> 
</template>

<script>
import { useStore } from 'vuex'
import { computed, onMounted } from '@vue/runtime-core'
import Card from './components/Card'
import Carrito from './components/Carrito'

export default {
  name: 'App',
  components: {
    Card, Carrito
  },
  setup(){
    const store = useStore()
    onMounted(() => {
      store.dispatch('fetchData')
    })

     const productos = computed(() => store.state.productos)
    //  const carrito = computed(() => store.state.carrito)
     
     return{productos}

  }
}
</script>
