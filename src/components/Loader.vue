<template>
  <div class="loader">
    <div class="text ttu">{{ label }}</div>
    <slot></slot>
    <div class="text ttu">...Loading...</div>
  </div>
</template>

<script>
export default {
  name: "Loader",
  props: ["label"],
};
</script>

<style scoped lang="scss">
@import "@/styles/vars";
@import "@/styles/utilities";
@import "@/styles/mixins";

.loader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  @include df();
  flex-direction: column;
  background: $brand-background;
}

svg {
  width: 100px;
  margin: 2rem 0;
  fill: $text-primary;
  animation: pulse 0.5s infinite alternate;
}

@keyframes pulse {
  to {
    transform: scale(1.2);
  }
}

.text {
  color: $text-primary;
  letter-spacing: 2px;
}
</style>
