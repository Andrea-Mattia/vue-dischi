<template>
  <section class="main-content">
    MAIN CONTENT HERE
  </section>
</template>

<script>
export default {
  name: "MainContent",
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/mixins";

.main-content {
  @include df();
  height: calc(100vh - 70px);
  background: $brand-background;
}
</style>
