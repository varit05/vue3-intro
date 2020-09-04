<template>
  <div>
    <img src="./logo.png">
    <p>spaces Left: {{ spacesLeft }} out of {{ capacity }}</p>
    <button @click="inc">Increase capacity</button>
    <h2>Attending</h2>
    <ul>
      <li v-for="(name, index) in attending" :key="index">{{name}}</li>
    </ul>
  </div>
</template>

<script>
import { reactive, computed, toRefs } from "vue";

export default {
  setup() {
    const event = reactive({
      capacity: 3,
      attending: ["Varit", "Trupti", "Sanket"],
      spacesLeft: computed(() => {
        return event.capacity - event.attending.length;
      })
    });
    const inc = () => {
      capacity.value++;
    };
    return {
      ...toRefs(event),
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
