<template>
  <nav>
    <router-link to="/">Home</router-link>
    <div v-if="store.getters.getAuthStatus">
      <router-link to="/dashboard">Dashboard</router-link> |
      <router-link to="/account">Account</router-link>
    </div>
    <div v-else>
      <router-link to="/login">Login</router-link> |
      <router-link to="/signup">SignUp</router-link>
    </div>
    
    
  </nav>
  <router-view/>
</template>

<script>
import { onBeforeMount } from 'vue';
import { useStore } from 'vuex';

export default {
  name: 'App',
  setup() {
    const store = useStore()

    onBeforeMount(() => {
      store.commit('onInit')
    })

    return {
      store,
    }
  }
}

</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
