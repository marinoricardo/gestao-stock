<template>
  <v-app id="inspire">
 <v-navigation-drawer
      class="deep-purple accent-4"
      dark
      v-model="drawer"
      app
    >
      <v-list>
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <template v-slot:append>
        <div class="pa-2">
          <v-btn block>
            Sair
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Dashboard</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <!--  -->
      <router-view/>
    </v-main>
      <v-footer >
    <v-col
      class="text-center"
      cols="12"
    >
      {{ new Date().getFullYear() }} — <strong>Marino Ricardo</strong>
    </v-col>
  </v-footer>
  </v-app>
</template>

<script>
  export default {
    data: () => (
      { drawer: null,
      items: [
          { title: 'Inicio', icon: 'mdi-view-dashboard', to: '/' },
          { title: 'Produtos', icon: 'mdi-account-box', to: '/productos' },
          { title: 'Vendas', icon: 'mdi-gavel' , to: '/vendas'},
          { title: 'Relatorios', icon: 'mdi-account-box',to: '/relatorios' },
          { title: 'Sobre', icon: 'mdi-account-box',to: '/about' },
        ],
      }),
    
  }
</script>