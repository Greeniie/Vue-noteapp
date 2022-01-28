<template>
<div class="my-10 mx-10">
      <v-card shaped height="400px" width="300px">
            <v-card-title class="blue lighten-5">{{ note.title }}</v-card-title>
            <v-card-text class="py-5">{{ note.body }}</v-card-text>
            <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
          class="button"
            color="red"
            text
            @click="onDelete(note.id)"
          >
            Delete
          </v-btn>
        </v-card-actions>
        </v-card>
</div>
   
</template>

<script>
export default {
    name: 'Note',
    props: {
        note: Object,
    },
    methods: {
        onDelete(id) {
            this.$emit('delete-note', id)
        }
    }
}
</script>

<style scoped>
.button {
   position: absolute;
   bottom: 10px;
   right: 10px;
}
</style>