<template>
  <router-link :to="{ name: 'edit', params: { id, link, name } }">
    <div class="card">
      <img :src="link" :alt="name" />
      <p>{{ name }}</p>
    </div>
  </router-link>
</template>

<script>
export default {
  name: 'Card',
  props: ['link', 'name', 'id'],
};
</script>

<style scoped>
.card {
  border-radius: var(--radius);
  cursor: pointer;
  transition: 0.2s all ease-in-out;
}

.card img {
  width: 100%;
  aspect-ratio: 1;
  border-radius: var(--radius);
  border: 5px var(--dark-olive) solid;
}

.card:hover {
  box-shadow: 0px 0px 15px 0px var(--lime);
  transform: translateY(-10px);
}

.card:hover p {
  bottom: 0;
  opacity: 0.9;
}

p {
  position: absolute;
  bottom: -20px;
  opacity: 0;
  transition: 0.2s all ease-in-out;
  width: 100%;
  padding: 10px;
  background: var(--black);
  border-radius: 0 0 var(--radius) var(--radius);
  text-align: center;
}
</style>
