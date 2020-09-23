<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
      <!-- <router-link to="/home-old">Homeold</router-link> -->
    </div>
    <router-view />
    <h3>@root :{{ user.username }} - {{ fullname }}</h3>
    <strong>Followers: {{ followers }}</strong>
    <button @click="followUser">Follow</button>
  </div>
</template>


<script>
export default {
  name: "App",
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "Shyniben",
        firstname: "Shyniben",
        lastname: "Koyakkil",
        email: "shyniben@gmail.com",
        isAdmin: true
      }
    };
  },
  watch: {
    followers(newFollowCount, oldFollowCount) {
      if (oldFollowCount < newFollowCount) {
        console.log(`${this.user.username} has gained a follower!`);
      }
    }
  },
  computed: {
    fullname() {
      return `${this.user.firstname} ${this.user.lastname}`;
    }
  },
  methods: {
    followUser() {
      this.followers++;
    }
  },
  mounted() {
    this.followUser();
  }
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
