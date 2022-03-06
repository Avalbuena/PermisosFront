<template>
    <div>
        <h1>Permisos</h1>
        <br>
        <hr>
        <table class="table table-hover">
            <thead>
            <tr>
                <td>ID</td>
                <td>Primer Nombre</td>
                <td>Segundo Nombre</td>
                <td>Tipo de Permiso</td>
                <td>Fecha del Permiso</td>
            </tr>
            </thead>

            <tbody>
                <tr v-for="item in items" :key="item.permitId">
                    <td>{{ item.permitId }}</td>
                    <td>{{ item.firstName }}</td>
                    <td>{{ item.lastName }}</td>
                    <td>{{ item.permitTypeName }}</td>
                    <td>{{ item.permitDate }}</td>
                    <td><router-link :to="{name: 'Edit', params: { id: item.permitId }}" class="btn btn-primary">Editar</router-link></td>
                    <!-- <td><button class="btn btn-danger"  v-on:click="deleteItem(item.permitId)">Borrar</button></td> -->
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

import axios from 'axios'

export default {
  data () {
    return {
      items: []
    }
  },

  created: function () {
    this.fetchItems()
  },

  methods: {
    fetchItems () {
      const uri = 'http://localhost:6303/api/permit/getallpermit'
      axios.get(uri).then((response) => {
        this.items = response.data
        console.log(response.data)
      })
        .catch(function (error) {
          // handle error
          console.log(error)
        })
        .then(function () {
          // always executed
        })
    }
  }
}
</script>
