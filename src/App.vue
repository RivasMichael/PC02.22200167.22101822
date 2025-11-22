
<template>
  <LoginComponent v-if="!token" @login-success="onLoginSuccess" />
  <div v-else>
    <DigimonList />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import LoginComponent from './components/auth/LoginComponent.vue';
import DigimonList from './components/digimon/DigimonList.vue';

const token = ref('');

function onLoginSuccess(receivedToken) {
  token.value = receivedToken;
}
</script>
