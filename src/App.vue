
<script setup>
import {ref,computed} from 'vue'

  const name = 'libre sooy';
  const counter = ref(0);
  const increment = ()=> {
    console.log('aumentar contador');
    counter.value++;
    console.log(counter);
  }

  const decrement = () =>  counter.value--;

  const reset = () =>  counter.value = 0;

  const calssCounter = computed(() => { 
    if(counter.value === 0)
    {
      return 'zero';
    }
    if (counter.value > 0) 
    {
      return 'positive';  
    }
    if (counter.value < 0) 
    {
      return 'negative';  
    }
   })

  const inactivo = ref(false);
  let array = ref([]);

  const ingresarValor = () =>
  {
    array.value.push(counter.value);
  }
  const classComprobar = computed (() =>
  {
    array.value.includes(counter.value) ? inactivo.value=true : inactivo.value = false;
  })


</script>
<template>
  <div class="container text-center">
    <h1>Hola vue js {{ name.toUpperCase() }} </h1>

    <h2 :class="calssCounter">{{ counter }} </h2>

    <button @click="increment" class ="btn btn-success">aumentar</button>
    <button @click="decrement" class="btn btn-danger">disminuir</button>
    <button @click="reset" class="btn btn-secondary">Reset</button>
    <button @click="ingresarValor" :disabled="inactivo" class="btn btn-primary"> agregar</button>

    <h2 :class="classComprobar">{{ array }} </h2>

    <!-- //BOTONES -->
    <!-- <button v-on:click.right="click('activame uno gaa')">button right</button>
    <button @:click="click('activame uno gaa')">button left</button>
    <button @:click.middle="click('activame uno gaa')">butten middel</button> -->
  </div>
  

</template>
<style>
  h1 
  {
    color:red;
  }
  .positive
  {
    color: green;
  }
  .negative 
  {
    color:blue;
  }
  .zero
  {
    color:peru;
  }
</style>