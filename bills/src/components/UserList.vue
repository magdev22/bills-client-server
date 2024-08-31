<template>
    <div>
      <h1>Список пользователей</h1>
      <ul>
        <li v-for="user in users" :key="user.id">{{ user.name }}</li>
      </ul>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref, onMounted } from 'vue';
  
  interface User {
    id: number;
    name: string;
  }
  
  export default defineComponent({
    name: 'UserList',
    setup() {
      const users = ref<User[]>([]);
  
      onMounted(async () => {
        try {
          const response = await fetch('http://localhost:8080/user');
          const data = await response.json();
          users.value = data;
        } catch (error) {
          console.error('Ошибка при получении списка пользователей:', error);
        }
      });
  
      return {
        users,
      };
    },
  });
  </script>
  