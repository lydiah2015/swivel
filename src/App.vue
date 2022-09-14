<template>
  <nav class="navbar">
     <div class="logo">SWIVEL</div>
        <ul class="nav-links">
       <div class="menu">

      <li><router-link to="/">Home</router-link> </li>
      <li><router-link to="/about">About</router-link> </li>
      <li> <router-link to="/login">LogIn</router-link></li>
       <li> <router-link to="/orders">Orders</router-link></li>
 </div>
  </ul>
  
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

/* nav {
  padding: 50px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
} */
* {
 margin: 0;
 padding: 0;
 box-sizing: border-box;
}
body {
 font-family: cursive;
}
a {
 text-decoration: none;
}
li {
 list-style: none;
}
.navbar {
 display: flex;
 align-items: center;
 justify-content: space-between;
 padding: 20px;
 background-color: teal;
 color: #fff;
}
.nav-links a {
 color: #fff;
}
/* LOGO */
.logo {
 font-size: 32px;
}
/* NAVBAR MENU */
.menu {
 display: flex;
 gap: 1em;
 font-size: 18px;
}
.menu li:hover {
 background-color: #4c9e9e;
 border-radius: 5px;
 transition: 0.3s ease;
}
.menu li {
 padding: 5px 15px;
}


</style>
