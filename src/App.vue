<template>
  <div class="menu">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">Tombola</router-link>
    </nav>
  </div>
  <router-view />
  <footer>
    <h3>il footer</h3>
  </footer>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  width: 100%;
  padding: 50px 0;
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

}

nav a.router-link-exact-active {
  color: rgb(184, 184, 57);
}

footer {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
}

footer h3 {
  text-align: center;
}
</style>
