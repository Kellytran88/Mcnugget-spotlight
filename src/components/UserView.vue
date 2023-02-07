<template>
  <ThumbGrid :minion2="minion1"/>


</template>

<script>
import ThumbGrid from "./ThumbGrid.vue";

export default {
  name: "UserView",

  props: ["minion1"],

  components: {
    ThumbGrid,
}

};
</script>

<style>

</style>
