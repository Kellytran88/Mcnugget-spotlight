<template>
    <div id="userClass">
      <h2>Shapes</h2>
      <div class="thumbGrid">
        <!-- v-for = for each image in my whole array of objet -->
        <img class="thumbGrid" v-for="i in minion2"
        :key="i.id"
        :src="i.imageUrl"
        :alt="i.title"
        @click="handleClick(i.id)"
        />
      </div>
    </div>
</template>

  <script>
  export default {
    name: "ThumbGrid",
    
    emits: ["shareId2"],
    props: ["minion2"],

    methods: {
      handleClick(id) {
        this.$emit("shareId2", id);
      },
    }

  };
  </script>
  
  <style>
#userClass .thumbGrid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  text-align: center;
}

#userClass .thumbGrid img {
  object-fit: cover;
  max-width: 100%;
  border-radius: 5%;
  aspect-ratio: 1 / 1;
  cursor: pointer;
  border: 1px solid blue
}


  </style>