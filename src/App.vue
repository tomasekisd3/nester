<template>
  <v-app>
    <v-app-bar
      app
      color="white"
      dark
      class="d-flex justify-start flex-row"
      style="height: 90px;"
    >
      <v-row>
        <v-col class="d-flex justify-start pb-0 mt-4 white" style="background-color: #47BCC2;" >
          <v-avatar color="white" size="82">
            <img
              style="width: 150px; height: 150px;"
              src="../src/assets/logo1.png"
            />
          </v-avatar>
          <!-- <p class="text-h4 mt-4">NESTER</p> -->
        </v-col>

        <v-col class="text-h2 mt-7" style="font-weight: 500;">
          <div style="color: #47BCC2;letter-spacing: 10px; font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;">NESTER</div>
        </v-col>
      </v-row>

      
    </v-app-bar>

    <v-main>
      <!-- <img
        src="../src/assets/logo1.png"
      /> -->
      <HelloWorld v-if="false"/>
      <citizen-register />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import CitizenRegister from './components/CitizenRegister';

export default {
  name: 'App',

  components: {
    HelloWorld,
    CitizenRegister
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>
.color-custom-default {
    color: #47BCC2,
}
</style>
