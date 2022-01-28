<template>
  <v-app>
   <Header @add-note = "addNote"/>
   <div class="container">
     <Notes @delete-note = "deleteNote" :notes="notes"/>

   </div>
  
  
  </v-app>
</template>

<script>
import Header from "./components/Header";
import Notes from "./components/Notes";
export default {
  name: 'App',

  components: {
    Header,
    Notes,
    
  },

  data() {
    return {
      notes: []
    }
  },

  methods: {

     async addNote(note) {
     const res = await fetch('api/notes', {
      method: 'POST',
      headers: {
        'Content-type' : 'application/json',
      },
      body: JSON.stringify(note)
     })

     const data = res.json()

      this.notes = [...this.notes, data]
    },

    async deleteNote(id) {

      if (confirm('Are you sure?')) {
        const res = await fetch(`api/notes/${id}`, {
        method: 'DELETE',
        
      })

      res.status == 200 ? ( this.notes = this.notes.filter((task) => task.id !==id)) :alert('Could not delete')

     
    }},

    async fetchNotes() {
     const res = await fetch('api/notes')

     const data = res.json()
     return data
    },

     async fetchNote(id) {
     const res = await fetch(`api/notes/${id}`)

     const data = res.json()
     return data
    }

  },
  

  emits: ['delete-note', 'add-note'],

  async created() {
    this.notes = await this.fetchNotes()
  }
};


</script>

<style>
.container {
  width: 85%;
  margin: 100px auto;
}

</style>
