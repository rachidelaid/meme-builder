<template>
  <div class="card">
    <img :src="link" :alt="name" />
    <p>{{ name }}</p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: ['link', 'name'],
};
</script>

<style scoped>
.card img {
  width: 100%;
  aspect-ratio: 1;
  border-radius: var(--radius);
  border: 1px var(--white) solid;
}

.card:hover p {
  bottom: 1px;
  opacity: 1;
}

p {
  position: absolute;
  bottom: -20px;
  opacity: 0;
  transition: 0.2s all ease-in-out;
  width: 100%;
  padding: 10px;
  background: var(--black);
}
</style>
