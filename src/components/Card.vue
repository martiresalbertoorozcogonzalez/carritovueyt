<template>
  <div class="col-12 md-2 col-md-4 mt-2 mb-2 p-2">
        <div class="card">
            <img :src="producto.thumbnailUrl" :alt="`imagen-${producto.title}`" class="card-img-top">
            <div class="card-body">
                <h5 class="card-title">{{producto.title}}</h5>
                <p class="card-text">${{producto.precio}}</p>
                <button class="btn btn-dark" @click="agregar(producto)">Comprar</button>
            </div>
        </div>
  </div>
</template>

<script>

import { useStore } from "vuex";

export default {
  props: ['producto'],
  setup(){
    const store = useStore()
    const agregar = producto => {
      store.dispatch('agregarAlCarro', producto)
    }
    return {agregar}
  }
}
</script>

<style>

</style>