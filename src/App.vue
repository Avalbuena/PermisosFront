<template>
  <div id="app" class="container">
    <div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand href="#">Permisos</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item :to="{ name: 'Create' }">Agregar Permiso</b-nav-item>
        <b-nav-item :to="{ name: 'Index' }">Todos los Permisos</b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
    <transition name="fade">
      <div class="gap">
        <router-view></router-view>
      </div>
    </transition>
  </div>
</template>

<script>

export default {
}
</script>

<style>
    .fade-enter-active, .fade-leave-active {
      transition: opacity .5s
    }
    .fade-enter, .fade-leave-active {
      opacity: 0
    }
    .gap {
      margin-top: 50px;
    }
</style>
