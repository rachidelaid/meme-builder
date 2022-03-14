<template>
  <section class="home">
    <div v-if="list" class="list">
      <Card
        v-for="img in list"
        :key="img.id"
        :link="img.url"
        :name="img.name"
      />
    </div>
  </section>
</template>

<script>
import { ref } from '@vue/reactivity';
import Card from '../components/Card.vue';

// import data from '../data.json';

export default {
  name: 'Home',
  components: {
    Card,
  },
  setup() {
    const list = ref('');

    fetch('https://api.imgflip.com/get_memes')
      .then((resp) => resp.json())
      .then(({ data }) => {
        list.value = data.memes;
      });

    return { list };
  },
};
</script>

<style scoped>
.home {
  padding: 2rem;
}

.list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1.5rem;
}
</style>
