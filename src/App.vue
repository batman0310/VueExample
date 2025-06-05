<template>
  <div id="app">
  {{ user.username }}-{{ fullName }}<br>
  <strong>Followers:</strong> {{ followers }}<br>
  <button @click="incrementFollower">
    Follow Me
  </button>
  <p>
      <input v-model="greeting" type="text" />
    </p>
    <p>
    {{ greeting }} ({{ greeting.length }})
  </p>
  <p>
    {{lovemsg}}
  </p>
  <p> 
    <img src="https://media.tenor.com/5IEDStMH6VYAAAAM/thumbs-up-kid.gif" v-if="love" alt="Thumbs Up" />
    <img src="https://media.tenor.com/-f7fklja4fkAAAAM/cry-cute.gif" v-else alt="Thumbs Down" />
    <br>
    <button @click="toggleLove">
     Toggle
    </button>
  </p>
  </div> 
  <section class="wrapper">
    <h1>In-Progress</h1>
    <ul>
      <li 
      v-for="assignment in assignments.filter(a => !a.completed)" 
      :key="assignment.id">
        <Label>
            {{ assignment.title }}
            <input type="checkbox" v-model="assignment.completed" />
        </Label>
      </li>
    </ul>   
  </section>
  <section class="wrapper">
    <h1>Completed</h1>
    <ul>
      <li 
      v-for="assignment in assignments.filter(a => a.completed)" 
      :key="assignment.id">
        <Label>
            {{ assignment.title }}
            <input type="checkbox" v-model="assignment.completed" />
        </Label>
      </li>
    </ul>   
  </section>
  
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      greeting: 'Hello Vue!',
      followers: 0,
      love: true,
      lovemsg: 'She loves me!',
      user:{
        username: 'SAK_HAN',
        firstname: 'sharoz',
        lastname: 'alam',
        email: 'sharoz.alam.khan@gmail.com',
        isAdmin: true,
      },
      assignments: [
        {title: 'Vue.js Basics',completed: false, id: 1},
        {title: 'Vue.js Components',completed: false, id: 2},
        {title: 'Vue.js Directives',completed: false, id: 3},

      ]
    }; 
  },
  watch: {
    followers(newValfollowers, oldValfollowers) {
      console.log(`Followers changed from ${oldValfollowers} to ${newValfollowers}`);
    }
  },
  computed: {
      fullName() {
        return `${this.user.firstname} ${this.user.lastname}`;
      }
  },
  methods: {
    incrementFollower() {
      this.followers++
    },
    toggleLove() {
      this.love = !this.love;
      this.lovemsg = this.love ? 'She loves me!' : 'She loves me not!';
      console.log(this.lovemsg);
    }
  },
  mounted() {
    this.incrementFollower(); // Increment followers when the component is mounted
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app li {
  list-style-type: none;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

</style>
