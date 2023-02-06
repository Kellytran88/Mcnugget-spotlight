<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label> 
        Title
        <input v-model="title" />
      </label>

      <label>
        Image URL
        <input v-model="imageUrl" />
      </label>

      <label class="grid2Col">
        Project Description
        <textarea v-model="description"></textarea>
      </label>

      <div class="grid2Col" style="text-align: center">
        <button type="submit">SUBMIT</button> 
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
    };
  },
  methods: {
    handleSubmit() {
      console.log("new chicken nugger form submitted")

      //create a new object
      let newForm = {title: this.title, imageURL: this.imageUrl, description: this.description};
      //send the createproject and object to the parent  
      this.$emit("createProject", newForm);

      // reset the form
      this.title = '';
      this.imageUrl = '';
      this.description = '';

      console.log(newForm)
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

.grid2Col {
  grid-column: 1 / span 2;
}
</style>
