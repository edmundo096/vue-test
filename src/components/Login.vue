<template>
  <div class="hello">
    <h1>Login</h1>
    <h3>{{ msg }}</h3>
    <div class="login-box">
      <input type="text" v-model="username">
      <input type="password" v-model="password">
      <button type="button" v-on:click="login">Login</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      msg: 'Please login',
      username: '',
      password: ''
    }
  },
  methods: {
    login: function () {
      if (this.isLoginValid()) {
        alert(`Login of ${this.username}`)
        this.$router.push('/')
      } else {
        this.msg = 'User or password not valid'
      }
    },
    isLoginValid () {
      const isValid = this.username.trim().length > 0 && this.password.trim().length > 0
      return isValid
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
.login-box {
  margin-left: auto;
  margin-right: auto;
  width: 25%;
  min-width: 300px;
}
input, button {
  display: block;
}
input {
  width: 100%
}
</style>
