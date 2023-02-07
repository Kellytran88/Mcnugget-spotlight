<template>
  <div id="App">
    <nav>
      <button @click="isAdmin = true" :class="{ active: isAdmin }">ADMIN</button>
      <button @click="isAdmin = false" :class="{ active: !isAdmin }" >USER</button>
    </nav>
    <h1>My favourite Chicken Nuggets</h1>
    
    <!-- if this thing is true then show admin otherwise show user -->
    <!-- @createProject = the EVENT, what to do -->
    <admin-view v-if="isAdmin" @createProject="addProject" />
    <user-view v-else 
      :minion1="allProjects"
      :theNugget1="nuggetStar"
      @shareId1="shareId"  />
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";
import ThumbData from "./ThumbData";


// this is what is export to view machine
export default {
  name: "App",
  components: {
    userView: UserView,
    adminView: AdminView,
  },

  data() {
    return {
      isAdmin: false,
      allProjects: ThumbData,
      nuggetStar: ThumbData[0]

    };
  },

  methods: {
    addProject(newForm) {
      //create a unique ID
      newForm.id = this.allProjects.length + 1;
      console.log(this.allProjects);
      this.allProjects.push(newForm);
    },

    shareId(id) {
      let nugget = this.allProjects.find(t => t.id === id);
      this.nuggetStar = nugget;
    },
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

h1 {
  font-family: monospace; 
  font-style: normal; 
  font-variant: small-caps; 
  font-weight: 700; 
  color: #422800;
  text-align: center;
}
</style>
