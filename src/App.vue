<template>
  <v-app>
    <v-app-bar app elevation="2" style="background-color: #0e0e0e;color: #7e7055;">
      <v-spacer></v-spacer>
      <v-toolbar-title><strong>Scav case Sim Beta</strong></v-toolbar-title>
      <v-spacer></v-spacer>
    </v-app-bar>
    <v-main>
      <SCS/>
    </v-main>
    <v-footer padless >
      <v-container class="pa-0">
        <v-row no-gutters dense align="center" justify="center">
          <v-btn icon href="https://www.tarkovsokuhou.com/" target="_blank">
            <v-icon size="24px">
              mdi-post
            </v-icon>
          </v-btn>
          <v-btn icon href="https://twitter.com/TarkovSokuhou" target="_blank">
            <v-icon size="24px">
              mdi-twitter
            </v-icon>
          </v-btn>
          <v-btn icon href="https://www.youtube.com/channel/UCXPCa2zGd4pbsUDGRjY8uzA" target="_blank">
            <v-icon size="24px">
              mdi-youtube
            </v-icon>
          </v-btn>
        </v-row>
        <v-row no-gutters dense align="center" justify="center">ScavcaseSim by タルコフ速報</v-row>
      </v-container>
    </v-footer>
  </v-app>
</template>

<script>
import SCS from './components/SCS.vue'

export default {
  name: 'App',

  components: {
    SCS,
  },

  data: () => ({
    //
  }),
}
</script>
