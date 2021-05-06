<template>
  <header class="main-header">
    <img src="../assets/logo.png" alt="spotify-logo" />
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/mixins";
.main-header {
  @include df("vertical");
  height: 70px;
  background: $brand-color;
  img {
    height: 50px;
    margin-left: 0.5rem;
  }
}
</style>
