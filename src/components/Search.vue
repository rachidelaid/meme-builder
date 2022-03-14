<template>
  <form class="search" @submit.prevent="filter">
    <input id="term" type="text" />
    <button type="submit">
      <svg viewBox="0 0 24 24">
        <path
          fill="currentColor"
          d="M9.5,3A6.5,6.5 0 0,1 16,9.5C16,11.11 15.41,12.59 14.44,13.73L14.71,14H15.5L20.5,19L19,20.5L14,15.5V14.71L13.73,14.44C12.59,15.41 11.11,16 9.5,16A6.5,6.5 0 0,1 3,9.5A6.5,6.5 0 0,1 9.5,3M9.5,5C7,5 5,7 5,9.5C5,12 7,14 9.5,14C12,14 14,12 14,9.5C14,7 12,5 9.5,5Z"
        />
      </svg>
    </button>
  </form>
</template>

<script>
export default {
  name: 'Search',
  props: ['filter'],
};
</script>

<style scoped>
.search {
  display: flex;
  align-items: center;
  border: 2px var(--dark-olive) solid;
  border-radius: var(--radius);
  margin-bottom: 2rem;
  padding: 0.2rem;
}

input,
button {
  background: transparent;
  color: var(--white);
  border: none;
  outline: none;
}

input {
  width: 100%;
  font-size: 1.2rem;
  font-family: var(--head-font);
}

svg {
  color: var(--olive);
  width: 24px;
  cursor: pointer;
}

svg:hover {
  color: var(--lime);
}
</style>
