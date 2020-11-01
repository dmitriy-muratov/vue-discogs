<template>
  <div id="nav">
    <router-link to="/">Home</router-link>
    |
    <router-link to="/about">About</router-link>
    |
    <router-link to="/login">Login</router-link>
  </div>
  <component :is="layout">
    <router-view />
  </component>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import EmptyLayout from '@/layouts/EmptyLayout.vue';
  import MainLayout from '@/layouts/MainLayout.vue';

  export default defineComponent({
    computed: {
      layout(): string {
        return 'layout--' + (this.$route.meta.layout || 'empty');
      }
    },
    components: {
      EmptyLayout,
      MainLayout
    }
  });
</script>

<style lang="scss">
  @import '~materialize-css/dist/css/materialize.min.css';

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
