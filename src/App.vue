<template>

  <div id="app">
    <div id="nav">
      <router-link v-bind:to="{ name: 'login' }">Login</router-link>&nbsp;|&nbsp;
      <router-link v-bind:to="{ name: 'home' }">Home</router-link>&nbsp;|&nbsp;
      <router-link v-bind:to="{ name: 'profile' }">Profile</router-link>;
      <router-link v-bind:to="{ name: 'settings2' }">Settings</router-link>&nbsp;|&nbsp;
      
      <!-- <router-link v-bind:to="{ name: 'logout' }" v-if="$store.state.token != ''">Logout</router-link>&nbsp;|&nbsp; -->
    </div>
    <router-view />
  </div>
  
</template>

<style scoped>

#app{
  background-color: #1B1B3A;
  justify-content: center;
  height: 100vh;
  width: auto;
}

@import url('https://fonts.googleapis.com/css2?family=Antonio&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Julius+Sans+One&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Sulphur+Point&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Kodchasan&display=swap');

</style>
