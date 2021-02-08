<template>
  <div class="vue-tempalte">
    <form>
      <h3>Sign In</h3>

      <div class="form-group">
        <label>Email address</label>
        <input
          required
          type="email"
          v-model.trim="user.email"
          class="form-control form-control-lg"
        />
      </div>

      <div class="form-group">
        <label>Password</label>
        <input
          required
          type="password"
          v-model.trim="user.password"
          class="form-control form-control-lg"
        />
      </div>

      <button
        type="button"
        v-on:click="loginUser"
        class="btn btn-dark btn-lg btn-block"
      >
        Sign In
      </button>

      <p class="forgot-password text-right mt-2 mb-4">
        <router-link to="/forgot-password">Forgot password ?</router-link>
      </p>
    </form>
  </div>
</template>



<script>
import axios from "axios";
export default {
  mounted() {
    console.log("............login is mounted.");
  },

  data() {
    return {
      user: {
        name: "",
        email: "",
      },
    };
  },

  methods: {
    loginUser() {
      let self = this.user;
      let router = this.$router;
      axios
        .post("http://localhost:8000/login", {
          email: self.email,
          password: self.password,
        })
        .then(function (response) {
          self.response_key = response.data.result;
          router.push('/dashboard');
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>