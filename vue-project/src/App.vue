<script>
import Users from "./components/Users.vue";

export default {
  components: { Users },
  data() {
    return {
      users: [],
      error: "",
      userName: "",
      userMail: "",
      userPass: "",
    };
  },
  methods: {
    sendData() {
      if (this.userName == "") {
        return (this.error = "Name is required");
      } else if (this.userMail == "") {
        return (this.error = "Email is required");
      } else if (this.userPass == "") {
        return (this.error = "Password is required");
      }

      this.error = "";

      this.users.push({
        name: this.userName,
        email: this.userMail,
        password: this.userPass,
      });
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    },
  },
};
</script>

<template>
  <input type="text" v-model="userName" placeholder="Name" />
  <input type="email" v-model="userMail" placeholder="Email" />
  <input type="password" v-model="userPass" placeholder="Password" />
  <p>{{ error }}</p>
  <button @click="sendData()">Send</button>

  <div v-if="users.length == 0">Empty</div>

  <div v-else>You have {{ users.length }} users</div>

  <users
    v-for="(el, index) in users"
    :key="index"
    :user="el"
    className="user"
    :index="index"
    :deleteUser="deleteUser"
  />
</template>

<style scoped>
div {
  border: 1px solid black;
  padding: 10px;
}
</style>
