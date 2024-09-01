
<template>
  <header>
    <img alt=" logo" class="logo" src="" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/user">Список юзеров</RouterLink>
        <RouterLink to="/user/:id">Детали юзера</RouterLink>
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
import TheWelcome from './components/TheWelcome.vue';

export default defineComponent({
  name: 'App',
  components: {
    TheWelcome
  },
});
</script>
