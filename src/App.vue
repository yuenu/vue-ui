<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">UI Demo</router-link>
  </div>
  <router-view/>
  <ScrollTop />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ScrollTop from '@/components/ScrollTop.vue'
export default defineComponent({
  components: {
    ScrollTop
  }
})
</script>

<style lang="scss">
* {
  margin:0;
  padding:0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
