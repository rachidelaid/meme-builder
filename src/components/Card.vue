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
.card {
  border-radius: var(--radius);
  cursor: pointer;
}

.card img {
  width: 100%;
  aspect-ratio: 1;
  border-radius: var(--radius);
  border: 1px var(--white) solid;
}

.card:hover {
  box-shadow: 0px 0px 15px 0px var(--lime);
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
