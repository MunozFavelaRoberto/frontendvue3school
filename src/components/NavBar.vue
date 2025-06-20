<template>
    <v-app-bar app color="indigo" dark>
      <v-toolbar-title>Mi Portal</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn text :to="'/'" tag="RouterLink">Inicio</v-btn>
      <v-btn text :to="'/login'" tag="RouterLink">Login</v-btn>
      <v-btn text :to="'/configuracion'" tag="RouterLink">Configuración</v-btn>

    </v-app-bar>
</template>