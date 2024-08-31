<template>
  <div>
    <h1>Список пользователей</h1>
    <div class="user-cards">
      <div v-for="user in users" :key="user.id" class="user-card">
        <h2>{{ user.name }} {{ user.surname }}</h2>
        <p>Bill: {{ user.bill }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';

interface User {
  id: number;
  name: string;
  surname: string;
  bill: number;
}

export default defineComponent({
  name: 'UserList',
  setup() {
    const users = ref<User[]>([]);
    const route = useRoute();

    onMounted(async () => {
      try {
        const id = route.params.id;
        const response = await fetch(`http://localhost:8080/user/${id}`);
        const data = await response.json();
        users.value = [data];
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

<style scoped>
.user-cards {
  display: flex;
  flex-wrap: wrap;
}

.user-card {
  border: 1px solid #d3d3d3;
  border-radius: 5px;
  padding: 10px;
  margin: 10px;
  width: 200px;
  background-color: #f0f8ff; /* Пастельный голубой */
  transition: all 0.3s;
}

.user-card:hover {
  transform: scale(1.05);
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

.user-card h2 {
  margin-bottom: 5px;
  color: #333;
}

.user-card p {
  font-size: 14px;
  color: #666;
}
</style>
