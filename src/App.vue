<template>
  <app-header></app-header>
        <div class="container">
          <router-view></router-view>
        </div>
</template>

<script setup>
  import { useCounterStore } from './stores/counter';
  const store = useCounterStore();

  store.$onAction(({
    name, /// name
    store, /// store instance,
    args, /// event,
    after, //hook
    onError, /// hook
  })=>{
    console.log(name)
    console.log(store)
    console.log(args)
    after((result)=>{ console.log(result)})
    onError((error)=>{ console.log(error)})
  },true)


</script>