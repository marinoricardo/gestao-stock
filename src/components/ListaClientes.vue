<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
            <th class="text-left">
                #
            </th>
          <th class="text-left">
            Nome
          </th>
          <th class="text-left">
            E-mail
          </th>
          <th class="text-left">
            Contacto
          </th>
          <th class="text-left">
           Website
          </th>
          <th class="text-left">
           Cidade
          </th>
          <th class="text-left">
              Accao
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(item,index) in clientes"
          :key="index"
        >
          <td>{{ index + 1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.email }}</td>
          <td>{{ item.phone }}</td>
          <td>{{ item.website }}</td>
          <td>{{ item.address.city }}</td>
          <td>
                 <v-btn
                    class="mx-2"
                    fab
                    dark
                    small
                    color="cyan"
                    @click="editar"
                    >
                    <v-icon dark>
                        mdi-pencil
                    </v-icon>
                </v-btn>
          </td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
  export default {
    data () {
      return {
      }
    },
    props: {
        clientes: Array
    },
    methods: {
        editar(){
            alert("Clicou em Editar")
        }
    }
  }
</script>

