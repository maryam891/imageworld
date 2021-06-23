<template>
  <div class="searchbox">
    <input
      type="text"
      v-model="search"
      class="searchbar"
      style="width: 600px;
        height:40px
  ;"
    />
    <input type="button" value="search" @click="onClick" class="button" />
    <searchphotos :dicons="icons" />
  </div>
</template>
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
<script>
import searchphotos from "../components/searchphotos.vue";
export default {
  name: "home",
  components: { searchphotos },
  data() {
    return {
      icons: null,
      search: null,
    };
  },
  methods: {
    onClick() {
      if (this.search != null) {
        fetch(
          "https://api.pexels.com/v1/search?size=small&query=" + this.search,
          {
            headers: {
              Authorization:
                "563492ad6f91700001000001d42c83bc2ebe4e8d9cc79617523031be",
            },
          }
        )
          .then((response) => response.json())
          .then((result) => {
            this.icons = result.photos;
          });
      } else {
        alert("Please write something!");
      }
    },
  },
};
</script>

<style>
.searchbar {
  background-color: rgb(240, 240, 240);
}
.searchbar {
  width: 300px;
  border: none;
  border-radius: 4px;
}
.searchbox {
  position: absolute;
  top: 50%;
  left: 25%;
  transform: translate(-50% -50%);
}
.button {
  background-color: rgba(51, 51, 51, 0.945);
  color: rgb(255, 245, 245);
  border-radius: 6px;
  height: 40px;
  width: 70px;
}
.button:hover {
  background-color: rgb(29, 28, 28);
  color: rgb(78, 78, 78);
}
.images {
  width: 30%;
  float: left;
  padding: 20px;
}
</style>
