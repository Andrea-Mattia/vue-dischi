<template>
  <form class="search">
    <label for="search">Select by genre:</label>
    <select
      @change="$emit('performSearch', searchGenre)"
      v-model="searchGenre"
      name="search"
      id="search"
    >
      <option selected value="all">All</option>
      <option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="metal">Metal</option>
      <option value="jazz">Jazz</option>
    </select>
  </form>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchGenre: "",
    };
  },
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/mixins";

.search {
  margin-top: 2rem;
  label {
    margin-right: 1rem;
    color: $text-primary;
  }
  select {
    width: 100px;
    height: 30px;
    padding-left: 0.5rem;
  }
}
</style>
