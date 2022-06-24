<template>
  <main>
    <div class="gArticle">
      <a
        class="filter"
        href="#"
        :class="{ filter__selected: filter === 'all' }"
        @click="filter = 'all'"
        >All</a
      >
      <a
        class="filter"
        href="#"
        :class="{ filter__selected: filter === 'remaining' }"
        @click="filter = 'remaining'"
        >Remaining</a
      >
      <a
        class="filter"
        href="#"
        :class="{ filter__selected: filter === 'done' }"
        @click="filter = 'done'"
        >Done</a
      >
    </div>
  </main>
</template>
<script>
export default {
  name: "TestOnLinks",
  data() {
    return {
      filter: "all",
    };
  },
};
</script>
<style lang="scss" scoped>
.filter {
  text-decoration: none;
  color: blueviolet;
  font-size: 2rem;
  &__selected {
    color: yellow;
  }
}
</style>
