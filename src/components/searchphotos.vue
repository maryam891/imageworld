<template>
  <div>
    <div v-for="(icon, index) in dicons" v-bind:key="index">
      {{ icon.photos }}
      <img :src="icon.src.large" class="images" />
    </div>
  </div>
</template>

<script>
export default {
  name: "searchphotos",
  props: ["dicons"],
};
</script>
