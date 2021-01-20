<template>
  <div>
    <h1>Sign In</h1>
    <form @submit.prevent="submit">
      <div>
        <label for="email">Email</label>
        <input type="email" name="email" id="email" v-model="form.email" />
      </div>
      <div>
        <label for="password">Password</label>
        <input type="password" name="password" id="password" v-model="form.password" />
      </div>
      <div>
        <button type="submit">Sign in</button>
      </div>
    </form>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "signin",
  data() {
    return {
      form: {
        email: "",
        password: ""
      }
    };
  },
  methods: {
    ...mapActions({
      signIn: "auth/signIn"
    }),
    submit() {
      this.signIn(this.form).then(() => {
        this.$router.replace({
          name: "dashboard"
        });
      });
    }
  },
  components: {}
};
</script>

<style>
</style>