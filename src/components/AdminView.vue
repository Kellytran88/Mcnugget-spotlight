<template>
  <div>
    <form id="form" @submit.prevent="handleSubmit">
      <label>
        McName
        <input type="text" v-model="title" />
      </label>

      <label>
        McPicture
        <input type="url" v-model="imageUrl" placeholder="https://" />
      </label>

      <label class="grid2Col">
        McAbout
        <textarea
          v-model="description"
          placeholder="Sharing is caring, tell us more about your nugget"
        ></textarea>
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
      console.log("new chicken nugget form submitted");

      //create a new object
      let newForm = {
        title: this.title,
        imageUrl: this.imageUrl,
        description: this.description,
      };
      //EVENT= send the createproject and object to the parent
      this.$emit("createProject", newForm);

      // reset the form
      this.title = "";
      this.imageUrl = "";
      this.description = "";
    },
  },
};
</script>

<style>
form {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  font-family: helvetica;
  margin: 20px 0px;
  padding: 0px 30px;
}

input,
textarea {
  display: block;
  width: 100%;
  margin: 10px 0px;
  border: 1px solid #292929;
  border-radius: 2.5px;
  padding: 5px;
  font-family: helvetica;
}

.grid2Col {
  grid-column: 1 / span 2;
}

.button {
  background-color: #ffbc0d;
  border: 2px solid #292929;
  border-radius: 30px;
  box-shadow: #292929 4px 4px 0 0;
  color: #292929;
  cursor: pointer;
  font-weight: 600;
  font-size: 18px;
  padding: 0 18px;
  line-height: 50px;
  margin: 5px 0px 10px;
}

#form button:hover {
  color: #ffbc0d;
  background-color: #da291c;
}

/* https://images.bauerhosting.com/legacy/lifestyle-legacy/97/65414/90b1f/f0375/58909/1f28a/f2086/IMG_0496_640x640.jpg?q=80&w=440 */
</style>
