
<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
  <div id="app">
    <UserList />
  </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import { RouterLink, RouterView } from 'vue-router'
import UserList from './components/UserList.vue';
import UserById from './components/UserById.vue';

export default defineComponent({
  name: 'App',
  components: {
    UserList,
    UserById,
  },
});
</script>
