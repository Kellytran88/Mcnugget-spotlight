<template>
  <div id="App">
    <nav>
      <h1>Secret life of Chicken Nuggets</h1>
      <div class="buttonGrid">
        <button @click="isAdmin = true" :class="{ active: isAdmin }">ADMIN</button>
        <button @click="isAdmin = false" :class="{ active: !isAdmin }" >USER</button>
      </div>
    </nav>

    
    <!-- if this thing is true then show admin otherwise show user -->
    <!-- @createProject = the EVENT, what to do -->
    <AdminView v-if="isAdmin" @createProject="addProject" />
    <UserView v-else 
      :minion1="allProjects"
      :theNugget1="nuggetStar"
      @shareId1="shareIdNug"  />
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
    UserView,
    AdminView,
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

    shareIdNug(id) {
      //this = my compoment i'm in
      //the component has a property call allprojects
      //and it's an array and an array has the function find
      //t=for each project, the id of the project have to match the id that I pass as an argument in my function shareIdNug
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
  padding: 15px;
  font-family: Helvetica Neue,Arial,Noto Sans,sans-serif;;
  color: #292929;
}

nav {
  display: flex;
  justify-content: space-between;

}

.buttonGrid {
  display: flex;
  justify-content: center;
  padding: 15px 0px;
  gap: 10px;
}

.active {
  color: red;
}

button {
  background-color: #ffbc0d;
  border: 2px solid #292929;
  border-radius: 10px;
  box-shadow: #292929 2px 2px 0 0;
  cursor: pointer;
  font-weight: 600;
  font-size: 12px;
  padding: 0 18px;
  line-height: 30px;
}



</style>
