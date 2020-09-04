<template>
  <div>
    <img src="./logo.png">
    <p>spaces Left: {{ spacesLeft }} out of {{ capacity }}</p>
    <button @click="inc">Increase capacity</button>
    <h2>Attending</h2>
    <ul>
      <li v-for="(name, index) in attending" :key="index">{{name}}</li>
    </ul>
    <search></search>
  </div>
</template>

<script>
import {
  ref,
  computed,
  onBeforeMount,
  onRenderTracked,
  onRenderTriggered,
  onMounted
} from "vue";

import search from "./components/search.vue";

export default {
  components: {
    search
  },
  setup() {
    onBeforeMount(() => {
      console.log("Before mount hook");
    });
    onMounted(() => {
      console.log("Before mount hook");
    });
    onRenderTracked(() => {
      console.log("Hooks to check dependancies to debug");
    });
    onRenderTriggered(() => {
      console.log("Hook to check dependancies that re render the component");
    });
    const capacity = ref(3);
    const attending = ref(["Varit", "Sanket", "Trupti"]);
    const inc = () => {
      capacity.value++;
    };
    const spacesLeft = computed(() => {
      return capacity.value - attending.value.length;
    });

    return {
      capacity,
      attending,
      spacesLeft,
      inc
    };
  }
};
</script>

<style scoped>
img {
  width: 200px;
}
h1 {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
