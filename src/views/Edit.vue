<template>
  <section class="about">
    <canvas class="canvas"></canvas>
    <div class="form">
      <input type="text" placeholder="Top Text" v-model="top" />
      <input type="text" placeholder="Bottom Text" v-model="bottom" />
      <button>SAVE</button>
    </div>
  </section>
</template>

<script>
import { ref } from '@vue/reactivity';
import { useRoute } from 'vue-router';
import { onMounted } from '@vue/runtime-core';
export default {
  setup() {
    const top = ref('');
    const bottom = ref('');

    const route = useRoute();
    const img = route.params.link;

    if (!img) {
      window.location.pathname = '/';
    }

    onMounted(() => {
      const canvas = document.querySelector('.canvas');
      const ctx = canvas.getContext('2d');

      canvas.width = 400;
      canvas.height = 400;

      const bg = new Image();
      bg.src = img;

      ctx.drawImage(bg, 0, 0, 400, 400);
    });

    return { top, bottom };
  },
};
</script>

<style scoped>
.about {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  padding: 2rem;
  place-items: center;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

input {
  background: transparent;
  color: var(--white);
  border: 2px solid var(--dark-olive);
  padding: 0.4rem;
  border-radius: 0.5rem;
  outline: none;
  width: 100%;
  font-size: 1.2rem;
  font-family: var(--head-font);
}

input:focus {
  border-color: var(--olive);
}

button {
  padding: 0.4rem;
  background-color: var(--olive);
  color: var(--white);
  border-radius: 0.5rem;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 700;
  transition: all 0.2s ease-in-out;
}

button:hover {
  transform: scale(1.05);
}

button:active {
  transform: scale(0.95);
}
</style>
