<template>
  <div>
    <h1 class="headertext">List of photographers</h1>

    <div
      v-for="(photographer, index) in photographers"
      v-bind:key="index"
      class="grapherlist"
    >
      <div style="width:100%;">
        {{ photographer.photographer }}
      </div>
      <img v-if="photographer.src.large !== ''" :src="photographer.src.large" />
    </div>
  </div>
</template>

<script>
export default {
  name: "photographers",

  async created() {
    const response = await fetch("https://api.pexels.com/v1/curated?page=10", {
      method: "GET",
      headers: {
        Authorization:
          "563492ad6f91700001000001d42c83bc2ebe4e8d9cc79617523031be",
      },
    });
    let result = await response.json();
    this.photographers = result.photos;
    console.log(this.photographers);
  },

  data() {
    return {
      photographers: null,
    };
  },
};
</script>
<style>
.headertext {
  text-align: center;
  margin: 100px;
  color: rgb(168, 165, 161);
}
.grapherlist {
  text-align: center;
  padding: 20px;
}
</style>
