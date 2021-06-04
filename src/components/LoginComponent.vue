<template>
  <div class="home">
    <form @submit.stop.prevent="login()">
      <div class="form-group">
        <label for="email">Email</label>
        <input
          type="email"
          name="email"
          class="form-control"
          id="email"
          aria-describedby="emailHelp"
          placeholder="Enter email"
          v-model="user.email"
          required
        />
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input
          type="password"
          name="password"
          class="form-control"
          id="password"
          aria-describedby="emailHelp"
          placeholder="Enter password"
          v-model="user.password"
          required
        />
      </div>

      <button type="submit" class="btn btn-primary">Login</button>
    </form>
  </div>
</template>

<script>
import { authService } from "../services/auth.service";
export default {
  name: "LoginComponent",
  data() {
    return {
      user: {},
    };
  },

  methods: {
    login() {
      authService.login(this.user).then((response) => {
        console.log(response);
        this.$router.push("/");
      });
    },
  },
};
</script>

<style scoped></style>
