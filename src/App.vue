<script setup>
import { ref } from "vue";
import UserForm from "./components/UserForm.vue";
import UserCard from "./components/UserCard.vue";


const users = ref([]);
function addUser(user) {
  users.value.push(user);
}
function deleteUser(index) {
  users.value.splice(index, 1);
}
function updateUser(index, updatedUser) {
  users.value[index] = updatedUser;
}
</script>
<template>
  <div id="app">
    <div class="user-section">
      <div class="user-form">
        <UserForm @addUser="addUser" />
      </div>
      <div class="user-cards">
        <div v-for="(user, index) in users" :key="index" class="user-card">
          <UserCard
            :user="user"
            @deleteUser="deleteUser(index)"
            @updateUser="updateUser(index, $event)"
          />
        </div>
      </div>
    </div>
  </div>
</template>
