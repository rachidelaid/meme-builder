<template>
  <section class="home">
    <h1>Meme Builder</h1>
    <Search :filter="filter" />
    <div v-if="list" class="list">
      <Card
        v-for="img in list"
        :key="img.id"
        :id="img.id"
        :link="img.url"
        :name="img.name"
      />
    </div>
  </section>
</template>

<script>
import { ref } from '@vue/reactivity';
import Card from '../components/Card.vue';
import Search from '../components/Search.vue';

export default {
  name: 'Home',
  components: {
    Card,
    Search,
  },
  setup() {
    const list = ref('');

    const filter = (e) => {
      const term = e.target.elements.term.value.trim();
      list.value = list.value.filter((img) =>
        img.name.toLowerCase().includes(term),
      );
    };

    fetch('https://api.imgflip.com/get_memes')
      .then((resp) => resp.json())
      .then(({ data }) => {
        list.value = data.memes;
      });

    return { list, filter };
  },
};
</script>

<style scoped>
.home {
  padding: 2rem;
}

h1 {
  font-family: var(--main-font);
  font-weight: 700;
  text-align: center;
  font-size: 4rem;
  margin-bottom: 2rem;
}

.list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1.5rem;
}
</style>
