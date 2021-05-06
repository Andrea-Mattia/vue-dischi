<template>
  <div class="album">
    <img :src="albumCard.poster" :alt="albumCard.title" />
    <h3 class="ttu">{{ albumCard.title }}</h3>
    <div class="author">{{ albumCard.author }}</div>
    <div class="year">{{ albumCard.year }}</div>
    <div class="genre">{{ albumCard.genre }}</div>
  </div>
</template>

<script>
export default {
  name: "AlbumCard",
  props: ["albumCard"],
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/mixins";

.album {
  @include df("vertical");
  flex-direction: column;
  padding: 1rem;
  height: 380px;
  background: $brand-color;
  h3 {
    font-size: 20px;
    text-align: center;
    color: $text-primary;
    margin: 1.5rem 0 1rem;
  }
  .author {
    font-size: 20px;
  }
  .author,
  .year {
    margin-bottom: 0.5rem;
    color: $text-secondary;
  }
  .genre {
    color: $text-primary;
  }
}
</style>
