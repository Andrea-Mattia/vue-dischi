<template>
  <section class="main-content">
    <div v-if="!loading" class="cards">
      <div v-for="(album, index) in albumList" :key="index" class="album">
        <AlbumCard :albumCard="album" />
      </div>
    </div>
    <div v-else class="loading">Loading...</div>
  </section>
</template>

<script>
import axios from "axios";
import AlbumCard from "@/components/AlbumCard.vue";
export default {
  name: "MainContent",
  components: {
    AlbumCard,
  },
  data() {
    return {
      apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
      albumList: [],
      loading: true,
    };
  },
  created() {
    this.getAlbums();
  },
  methods: {
    getAlbums() {
      axios
        .get(this.apiURL)
        .then((res) => {
          this.albumList = res.data.response;
          this.loading = false;
        })
        .catch((err) => {
          console.log("ERROR", err);
        });
    },
  },
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/mixins";

.main-content {
  @include df();
  height: calc(100vh - 70px);
  background: $brand-background;
  .cards {
    @include df();
    flex-wrap: wrap;
    margin-top: 1rem;
    .album {
      flex-basis: calc(100% / 8 - 2rem);
      margin: 0.5rem;
    }
  }
}
</style>
