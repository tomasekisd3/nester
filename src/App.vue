<template>
  <v-app>
    <v-app-bar
      app
      color="white"
      dark
      class="d-flex justify-start flex-wrap pt-4"
      extended
    >
      <v-col class="d-flex justify-start white" style="background-color: #47BCC2;" >
        <v-avatar color="white" size="82">
          <img
            style="width: 150px; height: 150px;"
            src="../src/assets/logo1.png"
          />
        </v-avatar>
        <!-- <p class="text-h4 mt-4">NESTER</p> -->
      </v-col>

      <v-col class="text-h2" style="font-weight: 500;">
        <div class="pt-7" style="color: #47BCC2;letter-spacing: 10px; font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;">NESTER</div>
      </v-col>

      
    </v-app-bar>

    <v-main>
      <!-- <img
        src="../src/assets/logo1.png"
      /> -->
      <HelloWorld v-if="false"/>
      <citizen-register v-if="!list" @register="routerAux($event)" />
      <nests-list v-if="list" @register="routerAux($event)" />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import CitizenRegister from './components/CitizenRegister';
import NestsList from './components/NestsList.vue';

export default {
  name: 'App',

  components: {
    HelloWorld,
    CitizenRegister,
    NestsList
  },

  data() {
    return {
       list: true
    }
  },
  methods: {
    routerAux(ruta) {
      if (ruta === 'list') this.list = true
      else if (ruta === 'register') this.list = false
      else if (ruta === 'cancel') this.list = false
    },
  },
};
</script>

<style scoped>
.color-custom-default {
    color: #47BCC2,
}
</style>
