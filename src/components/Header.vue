<template>
     <v-app-bar
     class="mb-6"
      app
      color="blue lighten-1"
      dark
    >
      <div class="d-flex align-center">
        <h1 class="white--text">Noteefy</h1>
      </div>

      <v-spacer></v-spacer>

     <ModalButton @add-note= "addNote"/>
    </v-app-bar>
</template>

<script>
import ModalButton from "./ModalButton";
export default {
    name: 'Header',
    components: {
        ModalButton
    },

    methods: {
      addNote(id) {
        this.$emit('add-note', id)
      }
    }
}
</script>
