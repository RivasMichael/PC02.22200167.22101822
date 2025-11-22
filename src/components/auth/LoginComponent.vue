<template>
  <q-card class="q-pa-md q-mx-auto" style="max-width: 400px;">
    <q-card-section>
      <div class="text-h6">Iniciar Sesión</div>
      <q-input v-model="email" label="Email" type="email" class="q-mb-md" />
      <q-input v-model="password" label="Contraseña" type="password" class="q-mb-md" />
      <q-btn label="Ingresar" color="primary" @click="login" :loading="loading" />
      <div v-if="error" class="text-negative q-mt-md">{{ error }}</div>
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: 'LoginComponent',
  data() {
    return {
      email: '',
      password: '',
      loading: false,
      error: ''
    }
  },
  methods: {
    async login() {
      this.loading = true;
      this.error = '';
      try {
        const response = await fetch('https://storedb-api.onrender.com/node-api/users/signin', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'accept': '*/*'
          },
          body: JSON.stringify({
            email: this.email,
            password: this.password
          })
        });
        const data = await response.json();
        if (response.ok && data.token) {
          this.$emit('login-success', data.token);
        } else {
          this.error = data.message || 'Credenciales incorrectas';
        }
        } catch {
          this.error = 'Error de conexión';
        }
      this.loading = false;
    }
  }
}
</script>

<style scoped>
.q-card {
  margin-top: 100px;
}
</style>
