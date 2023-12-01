<template>
  <div class="menu">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">Tombola</router-link>
    </nav>
  </div>
  <div class="main">
    <router-view />
  </div>
  <!-- <footer>
    <h3>il footer</h3>
  </footer> -->
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-family: 'Courgette', cursive;
}

.menu {
  width: 100%;
  padding: 35px 0;
  background-color: #A63F03;
}

nav {
  width: 50%;
  display: flex;
  justify-content: space-around;
  margin: 0 auto;
}

nav a {
  font-weight: bold;
  color: white;
  text-decoration: none;
  font-size: 1.3rem;
}

nav a.router-link-exact-active {
  color: rgb(184, 184, 57);
}

.main {
  overflow-y: auto;
  width: 100%;
  height: calc(100vh - 96px);
}

footer {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 1rem 0;
  background-color: red;
}

footer h3 {
  text-align: center;
}
</style>
