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
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  margin: 20px 0px;
  padding: 0px 100px;
  text-align: center;
  width: 75%;  
  margin: 20px auto;
}

p {
    width: 100%;
    text-align: left;
}

.grid2Col {
  grid-column: 1 / span 2;
}

#spotlightClass div.thumbGrid img {
  object-fit: cover;
  max-width: 100%;
  border-radius: 5%;
  aspect-ratio: 1 / 1;
  border: 2px solid #DA291C;
  box-shadow: #DA291C 4px 4px 0 0;
}




</style>