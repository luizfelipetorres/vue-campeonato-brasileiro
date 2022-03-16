<template>
  <div class="app-top-bar">
    <v-app-bar color="green lighten-1" dense dark app>
      <v-app-bar-nav-icon  @click="drawer = true"></v-app-bar-nav-icon>
      <v-toolbar-title>Campeonato Brasileiro ⚽</v-toolbar-title>
    </v-app-bar>

  <v-navigation-drawer v-model="drawer" absolute temporar>
      <v-list nav dens >
        <v-list-item-group v-model="group" active-class="light-green">
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Inicio</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-soccer</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Classificação</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  name: 'AppTopBar',
  
  data: () => ({
    drawer: false,
    group: null,
  }),
}
</script>

<style scoped>

</style>
