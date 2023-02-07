<template>
    <div id="spotlightClass">
        <div class="thumbGrid">
            <img 
            :src="theNugget2.imageUrl" 
            :alt="theNugget2.title"
            /> 
            <p>{{ theNugget2.description }}</p>
        </div>
    </div>

</template>

<script>
export default {
    name: "Spotlight",

    props: ["theNugget2"],
}
</script>

<style>
#spotlightClass div.thumbGrid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  text-align: center;
}

#spotlightClass div.thumbGrid img {
  object-fit: cover;
  max-width: 100%;
  border-radius: 5%;
  aspect-ratio: 1 / 1;
  border: 1px solid brown
}


</style>