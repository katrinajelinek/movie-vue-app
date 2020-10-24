<template>
  <div id="app">
    <nav class="main-nav overlay clearfix">
      <ul id="menu">
        <li class="nav-home nav-current" role="presentation">
          <router-link to="/movies">Movies</router-link>
        </li>
        <li class="nav-about-us" role="presentation" v-if="!isLoggedIn()">
          <router-link to="/signup">Signup</router-link>
        </li>
        <li class="nav-author-page" role="presentation" v-if="!isLoggedIn()">
          <router-link to="/login">Login</router-link>
        </li>
        <li class="nav-author-page" role="presentation" v-if="isLoggedIn()">
          <router-link to="/logout">Logout</router-link>
        </li>
      </ul>
    </nav>
    <router-view/>
  </div>
</template>

<script>

export default {
  methods: {
    isLoggedIn: function () {
      return localStorage.getItem('jwt');
    }
  }
};
</script>