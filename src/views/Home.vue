<template>
  <section class="home">
    <div class="list">
      <Card
        v-for="img in list"
        :key="img.id"
        :link="img.blank"
        :name="img.name"
      />
    </div>
  </section>
</template>

<script>
import { ref } from '@vue/reactivity';
import Card from '../components/Card.vue';

import data from '../data.json';

export default {
  name: 'Home',
  components: {
    Card,
  },
  setup() {
    const list = ref(data);

    return { list };
  },
};
</script>

<style scoped>
.list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 10px;
}
</style>
