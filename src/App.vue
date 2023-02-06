<template>
  <div id="App">
    <nav>
      <button @click="isAdmin = true" :class="{ active: isAdmin }">ADMIN</button>
      <button @click="isAdmin = false" :class="{ active: !isAdmin }" >USER</button>
    </nav>
    <h1>My favourite chicken Nuggets</h1>
    
    <admin-view v-if="isAdmin" @createProject="addProject" />
    <user-view v-else />
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  name: "adminForm",
  components: {
    userView: UserView,
    adminView: AdminView
  },
  data() {
    return {
      isAdmin: true,
      allProjects: []
    };
  },
  methods: {
    addProject(newForm) {
      this.allProjects.push(newForm);
      console.log(this.allProjects);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
#App {
  width: 800px;
  margin: 0 auto;
}

nav {
  display: flex;
  justify-content: flex-end;
}

nav button {
  margin: 5px;
}

.active {
  color: red;
}
</style>
