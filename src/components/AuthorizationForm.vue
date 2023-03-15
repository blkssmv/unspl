<template>
  <div class="form">
    <form @submit.prevent="login" class="form_content">
      <input type="text" v-model="username" placeholder="Логин" />
      <input type="password" v-model="password" placeholder="Пароль" />
      <button type="submit">Авторизоваться</button>
    </form>
  </div>
</template>


<script>
import axios from 'axios';
import router from '@/router';

export default {
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {


    login() {
      const route = {
        path: 'https://unsplash.com/oauth/authorize',
        query: {
          redirect_uri: 'http://localhost:8081/',
          client_id: process.env.VUE_APP_UNSPLASH_ACCESS_KEY,
          response_type: 'code',
          scope: 'public+read_user+read_photos+write_photos+write_likes+write_followers+read_collections+write_collections'
        }
      };

      // Use Vue Router to navigate to the new URL
      router.replace(route);
    }
  }
}
</script>


<style lang="scss" scoped>
.form {
  display: flex;
  justify-content: center;
  width: 100%;
  padding: 50px 0;

  &_content {
    display: flex;
    flex-direction: column;
    max-width: 500px;
    width: 100%;
    gap: 15px;

    input {
      display: flex;
      width: 100%;
      padding: 10px;
      border: 2px solid teal;
      border-radius: 6px;

      &:focus {
        outline: none;
        border: 2px solid #0093e8;
        border-radius: 6px;
      }
    }

    button {
      cursor: pointer;
      transition: all .3s ease;
      align-self: flex-end;
      background-color: teal;
      color: #FFFFFF;
      padding: 10px 5px;
      width: 25%;
      border: none;
      border-radius: 6px;

      &:hover {
        background-color: #0093e8;
      }
    }
  }
}</style>