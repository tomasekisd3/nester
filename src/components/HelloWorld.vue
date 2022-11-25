<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Nester
        </h1>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" class="text-h4">
        Árbol
      </v-col>
      <v-col md="6" sm="12">
        <!-- letras numeros -->
        <v-text-field label="Código de árbol" />
      </v-col>
      <v-col md="6" sm="12">
        <v-text-field label="Fecha" />
      </v-col>
      <v-col md="6" sm="12">
        <v-text-field label="Hora" />
      </v-col>
      <v-col md="6" sm="12">
        <v-text-field label="Comuna" />
      </v-col>
      <v-col cols="12" class="text-h4">
        Nido
      </v-col>
      <v-col md="6" sm="12">
        <v-text-field label="Dirección" />
      </v-col>
      <v-col md="6" sm="12">
        <v-text-field label="Sector" />
      </v-col>
      <v-col md="6" sm="12">
        <v-text-field label="Coordenadas" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      ecosystem: [
        {
          text: 'vuetify-loader',
          href: 'https://github.com/vuetifyjs/vuetify-loader',
        },
        {
          text: 'github',
          href: 'https://github.com/vuetifyjs/vuetify',
        },
        {
          text: 'awesome-vuetify',
          href: 'https://github.com/vuetifyjs/awesome-vuetify',
        },
      ],
      importantLinks: [
        {
          text: 'Documentation',
          href: 'https://vuetifyjs.com',
        },
        {
          text: 'Chat',
          href: 'https://community.vuetifyjs.com',
        },
        {
          text: 'Made with Vuetify',
          href: 'https://madewithvuejs.com/vuetify',
        },
        {
          text: 'Twitter',
          href: 'https://twitter.com/vuetifyjs',
        },
        {
          text: 'Articles',
          href: 'https://medium.com/vuetify',
        },
      ],
      whatsNext: [
        {
          text: 'Explore components',
          href: 'https://vuetifyjs.com/components/api-explorer',
        },
        {
          text: 'Select a layout',
          href: 'https://vuetifyjs.com/getting-started/pre-made-layouts',
        },
        {
          text: 'Frequently Asked Questions',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
        },
      ],
    }),
  }
</script>
