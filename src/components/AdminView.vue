<template>
  <div>
    <form>
      <label> 
        Title
        <input v-model="title" />
      </label>
      <label>
        Image URL
        <input v-model="image" />
      </label>
      <label>
        Project Description
        <textarea v-model="description"></textarea>
      </label>
    </form>

    <button @click="handleSubmit">SUBMIT</button>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      title: "",
      image: "",
      description: "",
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("createProject", {
        title: this.title,
        image: this.image,
        description: this.description
      });
    }
  }
};
</script>

<style>
.viewColor {
  color: red;
}


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
</style>
