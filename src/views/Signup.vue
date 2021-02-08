<template>
  <div class="vue-tempalte">
    <form>
      <h3>Sign Up</h3>

      <div class="form-group">
        <label>Full Name</label>
        <input
          required
          type="text"
          v-model.trim="user.name"
          class="form-control form-control-lg"
        />
      </div>

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
        <label>Mobile Number</label>
        <input
          required
          type="text"
          v-model.trim="user.mobile"
          class="form-control form-control-lg"
        />
      </div>

      <div class="form-group">
        <label>Experience</label>
        <input
          required
          type="experience"
          v-model.trim="user.experience"
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
        :disabled="!isFormValid"
        v-on:click="registerIt"
        class="btn btn-dark btn-lg btn-block"
      >
        Register
      </button>

      <p class="forgot-password text-right">
        Already registered
        <router-link :to="{ name: 'login' }">sign in?</router-link>
      </p>
      <!-- <p class="text-center" red v-if="errors">
        Email Already Exist!
      </p> -->
    </form>
  </div>
</template>

<script>

    import axios from 'axios';
    // import { mapState } from "vuex";

    export default {
      
        mounted() {
            console.log('Component is mounted.');

        },

        data() {
          return {
            isExist: false,
            user: {
              name: "",
              email: "",
              mobile: "",
              experience: "",
              password: "",
            },
          };
        },
        computed:{
          isFormValid(){
            return (
                  this.user.name.length >2 &&
                  this.user.email.length >2 &&
                  this.user.mobile.length ==10 &&
                  this.user.experience.length >0 &&
                  this.user.password.length >2
            )
          }
        },
        methods: {
            registerIt() {
                let self = this.user;
                let router = this.$router;
                axios.post('http://localhost:8000/register' , {
                    name: self.name,
                    email: self.email,
                    phone:self.mobile,
                    exp:self.experience,
                    password: self.password
                }).then(function (response) {
                //     self.response_key = response.data.result;
                //     // this.$router.push('/');
                        console.log('here',this);
                        console.log(response);
                        if (response.data.status == 'exist') {
                          console.log('email exist')
                          // this.isExist = true;
                        }
                        router.push('/');

                }).catch(function (error) {
                        console.log('Error',error);
                });
            }
        }
    }
</script>