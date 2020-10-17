<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>

        <q-toolbar-title >
          Camara - Quasar
        </q-toolbar-title>

        
      </q-toolbar>
    </q-header>

      <q-footer class="bg-white" bordered>
      <q-tabs class="text-grey-10" active-color="primary" indicator-color="primary">
        <q-route-tab name="Home" icon="mail" label="home" to="/" exact/>
        <q-route-tab name="Camera" icon="camera" label="Camara" to="/camera" exact/>
      </q-tabs>
      </q-footer>

    <q-page-container class="bg-grey-3">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  
  data () {
    return {

    }
  }
}
</script>
