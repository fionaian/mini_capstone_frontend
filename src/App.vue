<template>
  <div id="app">
    <!--   <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/test">Test</router-link>
      |
      <router-link to="/products/new">New Product</router-link>
      |
      <router-link to="/signup">Sign-Up</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
    </div> -->

    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">Snack Shop</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <!-- <li class="nav-item active">
            <a class="nav-link" href="#">
              Home
              <span class="sr-only">(current)</span>
            </a> -->
          <li class="nav-item">
            <router-link to="/" class="nav-link">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/products/new" class="nav-link">New Product</router-link>
          </li>
          <li class="nav-item">
            <!-- <a class="nav-link" href="#">Link</a> -->
            <router-link to="/signup" class="nav-link">Signup</router-link>
          </li>
          <!--  <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdown"
              role="button"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Dropdown
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdown">
              <a class="dropdown-item" href="#">Action</a>
              <a class="dropdown-item" href="#">Another action</a>
              <div class="dropdown-divider"></div>
              <a class="dropdown-item" href="#">Something else here</a>
            </div> -->
          <li class="nav-item">
            <router-link to="/login" class="nav-link">Login</router-link>
          </li>
          <li class="nav-item">
            <!-- <a class="nav-link disabled" href="#">Disabled</a> -->
            <router-link to="/logout" class="nav-link">Logout</router-link>
          </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
          <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" />
          <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
        </form>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<style>
#nav a {
  font-weight: bold;
  color: #2c3e50;
}

/*#nav a.router-link-exact-active {
  color: #42b983;
}*/

body {
  font-family: Futura, "Trebuchet MS", Arial, sans-serif;
}

.navbar-brand {
  font-family: "Monoton", cursive;
  font-size: 5em;
}
.navbar {
  margin-bottom: 2rem;
}
</style>
