<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__username">@{{ user.username }}</h1>
      <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
      <div class="user-profile__follower-count">
        <strong>Followers:</strong>
        {{ followers }}
      </div>
    </div>
    <div
      class="user-profile__tweet"
      v-for="tweet in user.tweets"
      :key="tweet.id"
    >
      {{ tweet.id }} {{ tweet.content }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserProfile',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'Shyniben',
        firstname: 'Shyniben',
        lastname: 'Koyakkil',
        email: 'shyniben@gmail.com',
        isAdmin: true,
        tweets: [
          {
            id: 1,
            content: 'tweeter is amazing',
          },
          {
            id: 2,
            content: "Dont't forget to subscribe",
          },
        ],
      },
    };
  },
  watch: {
    followers(newFollowCount, oldFollowCount) {
      if (oldFollowCount < newFollowCount) {
        console.log(`${this.user.username} has gained a follower!`);
      }
    },
  },
  computed: {
    fullname() {
      return `${this.user.firstname} ${this.user.lastname}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
  },
  mounted() {
    this.followUser();
  },
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

.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid sandybrown;
  text-align: center;
}

.user-profile__admin-badge {
  border: 1px solid sandybrown;
  border-radius: 5px;
  padding: 5px;
  margin-bottom: 5px;
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
