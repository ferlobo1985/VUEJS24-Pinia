<template>
  <div class="row">
    <h1>Admin</h1>
    <hr />
    <div class="col-sm-5">
      <p>
        <strong> Change count:{{ count }} </strong>
      </p>

      <button type="button" class="btn btn-primary me-3" @click="store.add">+</button>
      <button type="button" class="btn btn-outline-secondary"  @click="store.subtract">-</button>

      <hr/>
      <p>{{ store.car.brand }}</p>
      <p>{{ store.car.color }}</p>
      <button
        type="button"
        class="btn btn-primary me-3"
        @click="patchState"
      >
        Patch state
      </button>

      <div>
        <hr/>
        <ul>
          <li v-for="(post) in store.posts">
            {{ post.title }}
          </li>
        </ul>
        <button
          type="button"
          class="btn btn-primary me-3"
          @click="store.getPosts(10)"
        >
          Get posts
        </button>

      </div>


    </div>
  </div>
</template>

<script setup>
  import { useCounterStore } from '@/stores/counter';
  import { computed } from 'vue';
  const store = useCounterStore();

  const count = computed(()=>store.getCount);

  // const add = () => store.counter++;
  // const subtract = () => store.counter--;

  const patchState = () => {
    store.$patch({
      counter:100,
      car:{
        brand:'Ford',
        color:'Red'
      }
    })
  }

  // store.$subscribe((mutation,state)=>{
  //   console.log(state);
  //   console.log(mutation.type);
  //   console.log(mutation.storeId);
  //   console.log(mutation.payload);
  // },{detached:true})


</script>