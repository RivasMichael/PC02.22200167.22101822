
<template>
  <LoginComponent v-if="!token" @login-success="onLoginSuccess" />
  <div v-else>
    <h2 style="text-align:center; color:#f7d358; margin-top:32px; font-family:'Pokemon Solid',Arial,sans-serif; text-shadow:2px 2px 0 #e65100;">Bienvenido, ya iniciaste sesión</h2>
    <!-- Aquí puedes agregar el componente de Digimons cuando lo creen -->
  </div>
</template>

<script setup>
import { ref } from 'vue';
import LoginComponent from './components/auth/LoginComponent.vue';

const token = ref('');

function onLoginSuccess(receivedToken) {
  token.value = receivedToken;
}
</script>
