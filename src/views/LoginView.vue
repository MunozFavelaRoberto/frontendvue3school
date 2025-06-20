<template>
      <!-- Círculos animados de fondo -->
      <ul class="circles">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>

      <v-container fluid class="fill-height d-flex align-center justify-center">
        <v-row class="elevation-10 rounded-lg bg-white overflow-hidden position-relative" style="max-width: 1200px;">
          <!-- Sección izquierda: Bienvenida -->
          <v-col cols="12" md="6" class="pa-10 d-flex flex-column justify-center text-white position-relative" style="background-color: #1669bb;">
            <div class="position-absolute inset-0" style="background: linear-gradient(to bottom, #263238, #37474f); opacity: 0.85;"></div>
            <div class="position-relative" style="z-index: 1;">
              <v-img
                src="https://static.wixstatic.com/media/dbaee8_453933def9284ef29a843fa1c7645a89~mv2.png/v1/crop/x_0,y_133,w_500,h_198/fill/w_500,h_198,al_c,q_85,enc_avif,quality_auto/Logotipos.png"
                max-width="600"
                class="mb-10"
                alt="Logo Universidad"
                contain
              />
              <h1 class="text-h4 font-weight-bold mb-2">Bienvenido al Portal Universitario</h1>
              <p class="text-body-1" style="color: #aed581;">
                Accede a tu cuenta institucional para administrar tu perfil académico, revisar calificaciones y estar al día con tus clases.
              </p>
              <v-btn class="mt-6 text-white" variant="outlined" style="border-color: #66bb6a; color: #66bb6a; background-color: transparent;" @click="$router.push('/registro')">
                ¿Eres nuevo? Regístrate aquí
              </v-btn>
            </div>
          </v-col>

          <!-- Sección derecha: Login -->
          <v-col cols="12" md="6" class="pa-10">
            <v-card flat>
              <v-card-title class="text-h5 text-center mb-6 text-primary">
                Iniciar sesión
              </v-card-title>
              <v-form @submit.prevent="login" ref="form" v-model="formValid">
                <v-text-field
                  v-model="email"
                  label="Correo institucional"
                  type="email"
                  prepend-inner-icon="mdi-email"
                  variant="outlined"
                  class="mb-4"
                  :rules="emailRules"
                  required
                />
                <v-text-field
                  v-model="password"
                  label="Contraseña"
                  type="password"
                  prepend-inner-icon="mdi-lock"
                  variant="outlined"
                  class="mb-4"
                  :rules="passwordRules"
                  required
                />
                <v-checkbox
                  v-model="rememberMe"
                  class="mb-4"
                  color="primary"
                >
                  <template #label>
                    <span class="text-body-2">Recordarme</span>
                  </template>
                </v-checkbox>
                <v-btn block color="primary" class="mt-2" type="submit">Iniciar sesión</v-btn>
              </v-form>
              <div class="text-center mt-4">
                <v-btn variant="text" >¿Olvidaste tu contraseña?</v-btn>
                <v-btn variant="text" color="primary">Recuperar</v-btn>
              </div>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      rememberMe: false,
      formValid: false,
      emailRules: [
        v => !!v || 'El correo es requerido',
        v => /.+@.+\..+/.test(v) || 'Debe ser un correo válido'
      ],
      passwordRules: [
        v => !!v || 'La contraseña es requerida',
        v => v.length >= 6 || 'Mínimo 6 caracteres'
      ]
    }
  },
  methods: {
    login() {
      if (this.$refs.form.validate()) {
        alert(`Iniciando sesión como: ${this.email}, Recordarme: ${this.rememberMe}`);
      }
    }
  }
}
</script>

<style scoped>
h1 {
  font-family: 'Merriweather', serif;
}

.circles {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: 0;
}
.circles li {
  position: absolute;
  display: block;
  list-style: none;
  width: 20px;
  height: 20px;
  background: rgba(28, 61, 252, 0.2);
  animation: animate 25s linear infinite;
  bottom: -150px;
  border-radius: 50%;
}
.circles li:nth-child(1) { left: 25%; width: 80px; height: 80px; animation-delay: 0s; }
.circles li:nth-child(2) { left: 10%; width: 20px; height: 20px; animation-delay: 2s; animation-duration: 12s; }
.circles li:nth-child(3) { left: 70%; width: 20px; height: 20px; animation-delay: 4s; }
.circles li:nth-child(4) { left: 40%; width: 60px; height: 60px; animation-delay: 0s; animation-duration: 18s; }
.circles li:nth-child(5) { left: 65%; width: 20px; height: 20px; animation-delay: 0s; }
.circles li:nth-child(6) { left: 75%; width: 110px; height: 110px; animation-delay: 3s; }
.circles li:nth-child(7) { left: 35%; width: 150px; height: 150px; animation-delay: 7s; }
.circles li:nth-child(8) { left: 50%; width: 25px; height: 25px; animation-delay: 15s; animation-duration: 45s; }
.circles li:nth-child(9) { left: 20%; width: 15px; height: 15px; animation-delay: 2s; animation-duration: 35s; }
.circles li:nth-child(10) { left: 85%; width: 150px; height: 150px; animation-delay: 0s; animation-duration: 11s; }

@keyframes animate {
  0% {
    transform: translateY(0) rotate(0deg);
    opacity: 1;
  }
  100% {
    transform: translateY(-1000px) rotate(720deg);
    opacity: 0;
  }
}
</style>