<template>
  <v-container class="grey lighten-5">
    <v-row no-gutters>
      <v-col order="last">
 <v-card
    class="mx-auto"
    max-width="344"
    outlined
    tile
  >
    <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title class="text-h5 mb-1">
          Clientes Cadastrados
        </v-list-item-title>
        <v-list-item-subtitle v-if="clientes.lenght == 10">{{ clientes.length }}</v-list-item-subtitle>
        <v-list-item-subtitle v-else>Sem Clientes</v-list-item-subtitle>
      </v-list-item-content>

    <v-icon
      large
      color="green darken-2"
    >
      mdi-domain
    </v-icon>
    </v-list-item>

  </v-card>
      </v-col>
      <v-col>
 <v-card
    class="mx-auto"
    max-width="344"
    outlined
    tile
  >
    <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title class="text-h5 mb-1">
          Vendas
        </v-list-item-title>
        <v-list-item-subtitle>1234</v-list-item-subtitle>
      </v-list-item-content>

    <v-icon
      large
      color="blue darken-2"
    >
      mdi-message-text
    </v-icon>
    </v-list-item>

  </v-card>
      </v-col>
      <v-col order="first">
 <v-card
    class="mx-auto"
    max-width="344"
    outlined
    tile
  >
    <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title class="text-h5 mb-1">
          Produtos
        </v-list-item-title>
        <v-list-item-subtitle>1234</v-list-item-subtitle>
      </v-list-item-content>

    <v-icon
      large
      color="orange darken-2"
    >
      mdi-arrow-up-bold-box-outline
    </v-icon>
    </v-list-item>

  </v-card>
      </v-col>
    </v-row>
    <v-row>
            <v-col
        cols="12"
        sm="6"
        md="8"
      >
      <h3 class="pa-2" width="100%">
        Lista de Clientes
      </h3>
      </v-col>
      <v-col
        cols="6"
        md="4"
      >

  <v-row justify="center">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
        class="ma-2"
        color="primary"
        v-bind="attrs"
        v-on="on"
        dark
      >
        Adicionar Cliente
        <v-icon
          dark
          right
        >
          mdi-checkbox-marked-circle
        </v-icon>
      </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">Cadastrar um novo Cliente</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal first name*"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal middle name"
                  hint="example of helper text only on focus"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal last name*"
                  hint="example of persistent helper text"
                  persistent-hint
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Email*"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Password*"
                  type="password"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
              >
                <v-select
                  :items="['0-17', '18-29', '30-54', '54+']"
                  label="Age*"
                  required
                ></v-select>
              </v-col>
              <v-col
                cols="12"
                sm="6"
              >
                <v-autocomplete
                  :items="['Skiing', 'Ice hockey', 'Soccer', 'Basketball', 'Hockey', 'Reading', 'Writing', 'Coding', 'Basejump']"
                  label="Interests"
                  multiple
                ></v-autocomplete>
              </v-col>
            </v-row>
          </v-container>
          <small>*indicates required field</small>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Fechar
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Salvar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
      </v-col>
      <v-col cols="12">
        <lista-clientes :clientes="clientes"/>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import ListaClientes from '../components/ListaClientes.vue'
import axios from 'axios'
export default {
  data(){
    return{
      dialog: false,
      clientes: []
    }
  },
  mounted(){
    this.getUsers()
  },
  components: {
    ListaClientes
  },
  methods: {
    getUsers(){
      axios.get('https://jsonplaceholder.typicode.com/users').then(res => {
        this.clientes = res.data
        console.log(res.lenght)
        console.log(this.clientes.length)
      })
    }
  }
}
</script>