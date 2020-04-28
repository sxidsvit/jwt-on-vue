<template>
  <div>
    <form @submit.prevent="login">
      <label for="email">email:</label>
      <input v-model="email" type="email" name="email" value />

      <label for="password">пароль:</label>
      <input v-model="password" type="password" name="password" value />

      <button type="submit" name="button">Войти</button>

      <p>{{ error }}</p>

      <router-link to="/register">Нет аккаунта? Зарегистрируйтесь</router-link>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    login() {
      this.$store
        .dispatch('login', {
          email: this.email,
          password: this.password
        })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
        .catch(err => {
          this.error = err.response.data.error
        })
    }
  }
}
</script>

<style scoped>
</style>
