<template>
  <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
</template>

<script>
import store from "../store";
import { onMounted, computed,ref } from "vue";

export default {
  name: 'HelloWorld',
  setup() {
    let count = ref(0);
    const countries = computed(() => store.state.countries);
    onMounted(() => store.dispatch("load"));

    const removeItem = (item) => store.commit("removeItem", item); 


    return {
      countries,
      removeItem,
      count
    };
  },
};

</script>
