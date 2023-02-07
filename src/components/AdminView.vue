<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label> 
        Nugget title
        <input type="text" v-model="title" />
      </label>

      <label>
        Nugget URL
        <input type="url" v-model="imageUrl" />
      </label>

      <label class="grid2Col">
        Nugget Description
        <textarea v-model="description"></textarea>
      </label>

      <div class="grid2Col" style="text-align: center">
        <button type="submit" class="button">SUBMIT</button> 
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "AdminView",

  data() {
    return {
      title: "",
      imageUrl: "",
      description: "",
      id: 0,
    };
  },

  methods: {
    handleSubmit() {
      console.log("new chicken nugget form submitted")

      //create a new object
      let newForm = {title: this.title, imageUrl: this.imageUrl, description: this.description};
      //EVENT= send the createproject and object to the parent  
      this.$emit("createProject", newForm);

      // reset the form
      this.title = '';
      this.imageUrl = '';
      this.description = '';
    }
  }
};
</script>

<style>

form {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  text-align: left;
}

input, textarea {
  display: block;
  width: 100%;
}

label {
  font-family: monospace; 
  font-size: 18px; 
  font-style: normal; 
  font-variant: small-caps; 
} 

.grid2Col {
  grid-column: 1 / span 2;
}

.button {
  background-color: #fbeee0;
  border: 2px solid #422800;
  border-radius: 30px;
  box-shadow: #422800 4px 4px 0 0;
  color: #422800;
  cursor: pointer;
  font-weight: 600;
  font-size: 18px;
  padding: 0 18px;
  line-height: 50px;
  margin: 5px 0px 10px;
}

button:hover {
  background-color: #fff;
}

/* https://images.bauerhosting.com/legacy/lifestyle-legacy/97/65414/90b1f/f0375/58909/1f28a/f2086/IMG_0496_640x640.jpg?q=80&w=440 */
</style>
