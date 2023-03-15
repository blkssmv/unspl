<template>
  <nav>
    <router-link to="/">Главная</router-link> 
    <router-link to="/profile">Профиль</router-link>
  </nav>
  <div class="container">
    <router-view/>
  </div>
  
</template>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
ul, ol, li{
  list-style: none;
} 
body{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #FFFFFF;
  font-size: 20px;
  
}

nav {
  padding: 15px;
  text-align: center;
  background-color: teal;
  a {
    margin: 0 50px;
    font-weight: bold;
    color: rgb(207, 158, 94);
    text-decoration: none;
    font-size: 25px;
    &.router-link-exact-active {
      text-decoration: underline;
      color: #FFFFFF;
    }
  }
}
.container{
  max-width: 1280px;
  padding: 10px;
  margin: 0 auto;
  height: 100vh;
}
</style>
