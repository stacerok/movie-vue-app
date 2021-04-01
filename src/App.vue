<template>
  <div id="app">
    <!-- <div id="nav"> -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <!-- <a class="navbar-brand" href="#">Navbar</a> -->
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNavDropdown"
        aria-controls="navbarNavDropdown"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <router-link to="/" class="nav-link">Home</router-link>
            <!-- <a class="nav-link" href="#">
              Home
              <span class="sr-only">(current)</span>
            </a> -->
          </li>
          <li class="nav-item">
            <router-link to="/movies" class="nav-link">All Movies</router-link>
            <!-- <a class="nav-link" href="#">Features</a> -->
          </li>
          <li class="nav-item">
            <router-link to="/movies/new" class="nav-link">Add a Movie</router-link>
            <!-- <a class="nav-link" href="#">Pricing</a> -->
          </li>
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdownMenuLink"
              role="button"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Account
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <router-link to="/login" class="dropdown-item">Login</router-link>
              <router-link to="/logout" class="dropdown-item">Logout</router-link>
              <router-link to="/signup" class="dropdown-item">Sign Up</router-link>
            </div>
          </li>
        </ul>
      </div>
    </nav>
    <div class="jumbotron jumbotron-fluid">
  <div class="container">
    <h1 class="display-4">Welcome to my movie site!</h1>
    <p class="lead">All movie lovers are welcome to add to the site.</p>
  </div>
</div>
    <!-- <router-link to="/">Home</router-link>
    |
    <router-link to="/movies">All Movies</router-link>
    |
    <router-link to="/movies/new">Add a Movie</router-link>
    |
    <router-link to="/signup">Sign Up</router-link>
    |
    <router-link to="/login">Login</router-link>
    |
    <router-link to="/logout">Logout</router-link> -->
    <!-- </div> -->
    <router-view />
  </div>
</template>

<style>
body {
  font-family: Candara, Calibri, Segoe, Segoe UI, Optima, Arial, sans-serif;
}
</style>
