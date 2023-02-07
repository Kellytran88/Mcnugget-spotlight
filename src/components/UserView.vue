<template>
  <Spotlight 
    :theNugget2="theNugget1"
  />

  <ThumbGrid 
    :minion2="minion1"
    @shareId2="shareId"
  />
</template>

<script>
import ThumbGrid from "./ThumbGrid.vue";
import Spotlight from "./Spotlight.vue";

export default {
  name: "UserView",

  props: ["minion1", "theNugget1"],

  emits: ["shareId1"],

  components: {
    ThumbGrid,
    Spotlight,
  },

  methods: {
    shareId(id) {
            console.log("userView" + id);
      this.$emit("shareId1", id); 

    }
  }
};
</script>

<style>
</style>
