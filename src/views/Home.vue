<template>
  <div class="home">
    <h1>Добро пожаловать в приложение!</h1>
    <div v-if="!loggedIn">
      Чтобы использовать это приложение, вам нужно
      <router-link to="/login">Войти</router-link>&nbsp;или
      <router-link to="/register">Зарегистрироваться</router-link>
    </div>
  </div>
</template>

<script>
import { authComputed } from '../vuex/helpers.js'
export default {
  computed: {
    ...authComputed
  }
}
</script>
