<template>
  <section class="main-content">
    <Search @performSearch="searchAlbum" />
    <div v-if="!loading" class="cards">
      <div
        v-for="(album, index) in filteredAlbumList"
        :key="index"
        class="album"
      >
        <AlbumCard :albumCard="album" />
      </div>
    </div>
    <Loader v-else label="Loading albums!">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
        <path d="M18 13 L26 2 8 13 14 19 6 30 24 19 Z" />
      </svg>
    </Loader>
  </section>
</template>

<script>
import axios from "axios";
import AlbumCard from "@/components/AlbumCard.vue";
import Loader from "@/components/Loader.vue";
import Search from "@/components/Search.vue";

export default {
  name: "MainContent",
  components: {
    AlbumCard,
    Loader,
    Search,
  },
  data() {
    return {
      apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
      albumList: [],
      loading: true,
      searchingAlbum: "",
    };
  },
  computed: {
    filteredAlbumList() {
      if (this.searchingAlbum === "all" || this.searchingAlbum === "") {
        return this.albumList;
      }

      return this.albumList.filter((album) => {
        return album.genre.toLowerCase() === this.searchingAlbum.toLowerCase();
      });
    },
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
    searchAlbum(opt) {
      this.searchingAlbum = opt;
    },
  },
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/mixins";

.main-content {
  @include df();
  flex-direction: column;
  height: calc(100% - 70px);
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
