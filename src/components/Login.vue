<template>
  <v-container fluid class="login-container">
    <!-- Imagen de fondo -->
    <v-img
      class="background-image"
      src="https://images.unsplash.com/1605902711622-cfb43c4437d1"
      cover
    >
      <div class="overlay"></div>

      <!-- Contenedor centrado -->
      <div class="center-wrapper">

        <!-- Card Login -->
        <v-card class="login-card" elevation="12">

          <!-- IMAGEN SUPERIOR -->
          <v-img
            src="https://imgs.search.brave.com/ldfTgAr4N_JQwGUAWBsN6XAM08tA9hDcRrqEEl5zfE4/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9zdGF0/aWMudmVjdGVlenku/Y29tL3N5c3RlbS9y/ZXNvdXJjZXMvdGh1/bWJuYWlscy8wNTkv/MDIyLzk0OC9zbWFs/bC9ibHVlLXNxdWFy/ZS11c2VyLXByb2Zp/bGUtaWNvbi1tb2Rl/cm4tYXBwLXVpLWRl/c2lnbi1lbGVtZW50/LWZyZWUtcG5nLnBu/Zw"
            max-width="220"
            class="mx-auto mb-4"
            contain
          ></v-img>

          <v-card-title class="text-center text-h5 font-weight-bold">
            Iniciar Sesión
          </v-card-title>

          <v-card-text>
            <v-form validate-on="submit lazy" @submit.prevent="submit">

              <!-- Usuario -->
              <v-text-field
                v-model="userName"
                :rules="rules"
                label="Usuario"
                prepend-inner-icon="mdi-account"
                variant="outlined"
                class="mb-3"
              ></v-text-field>

              <!-- Password -->
              <v-text-field
                v-model="password"
                :rules="rules"
                label="Contraseña"
                type="password"
                prepend-inner-icon="mdi-lock"
                variant="outlined"
                class="mb-3"
              ></v-text-field>

              <!-- Botón -->
              <v-btn
                :loading="loading"
                color="primary"
                class="mt-2"
                size="large"
                type="submit"
                block
                rounded="lg"
              >
                Entrar
              </v-btn>

            </v-form>
          </v-card-text>
        </v-card>

      </div>
    </v-img>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'

const loading = ref(false)
const userName = ref('')
const password = ref('')

const rules = [
  value => {
    if (!value) return 'Campo obligatorio'
    if (value.length < 4) return 'Mínimo 4 caracteres'
    return true
  }
]

async function submit () {
  loading.value = true

  const data = {
    user: userName.value,
    password: password.value
  }

  setTimeout(() => {
    loading.value = false
    alert(JSON.stringify(data, null, 2))
  }, 1200)
}
</script>

<style scoped>
.login-container {
  height: 100vh;
  padding: 0;
}

/* Fondo */
.background-image {
  height: 100vh;
}

/* Oscurecer fondo */
.overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    rgba(255, 255, 255, 1),
    rgba(254, 250, 250, 1)
  );
}

/* Centrado real */
.center-wrapper {
  position: relative;
  z-index: 2;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Card */
.login-card {
  width: 100%;
  max-width: 380px;
  border-radius: 18px;
  padding: 25px 20px;
  backdrop-filter: blur(6px);
}
</style>
