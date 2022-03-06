<template>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <h3>Add Item</h3>
      </div>
      <div class="card-body">
        <form v-on:submit.prevent="addItem">
          <div class="form-group">
            <label>Nombres:</label>
            <input type="text" class="form-control" v-model="item.name" required/>
          </div>
          <br>
          <div class="form-group">
            <label>Apellidos:</label>
            <input type="text" class="form-control" v-model="item.lastName" required />
          </div>
          <br>
           <div class="form-group">
            <label>Tipo de permiso:</label>
            <select class="form-control" v-model="item.permitType" required>
              <option value="0">
                [Seleccionar]
              </option>
              <option :value="item.id" v-for="item in items" :key="item.id">
                {{ item.description }}
              </option>
            </select>
          </div>
          <br>
          <div class="form-group">
            <label>Fecha:</label>
            <input type="date" class="form-control" v-model="item.permitDate" required />
          </div>
          <br>
          <div class="form-group">
            <input type="submit" class="btn btn-primary" value="Agregar Permiso" />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  data () {
    return {
      items: [],
      item: {}
    }
  },

  created: function () {
    this.fetchItems()
  },

  methods: {
    fetchItems () {
      const uri = 'http://localhost:6303/api/permittypes/getallpermittype'
      axios.get(uri).then((response) => {
        this.items = response.data
      })
        .catch(function (error) {
          // handle error
          console.log(error)
        })
        .then(function () {
          // always executed
        })
    },
    addItem () {
      const uri = 'http://localhost:6303/api/permit/registerpermit'
      axios.post(uri, this.item).then((response) => {
        console.log(this.item)
        console.log(response.data)
      })
    }
  }
}
</script>
