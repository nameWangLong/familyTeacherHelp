<template>
  <div id="app">
    <!-- <router-view/> -->
    welcome to this
    <ul v-for="(item,i) in users" :key="i">
      <li>账号：{{item.username}}</li>
      <li>密码：{{item.password}}</li>
      <li>工作：{{item.job}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      users: null
    };
  },
  created() {
    this.getUserInformation();
  },
  methods: {
    getUserInformation() {
      console.log("你好啊");
      this.$http.get("/api/user").then(response => {
        this.users = response.body._embedded.users;
      });
    }
  },
  components: {}
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
li {
  list-style: none;
  font-size: 18px;
  font-weight: 700;
}
</style>
