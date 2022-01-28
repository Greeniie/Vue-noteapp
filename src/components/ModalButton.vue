<template>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
      v-bind="attrs"
      v-on="on"
      class="ma-2"
      outlined
      small
      fab
      color="white"
    >
      <v-icon>mdi-pencil</v-icon>
    </v-btn>
      </template>

      <v-card shaped>
        <v-card-title class="blue lighten-5">
          <v-form
                ref="form"
                v-model="valid"
                lazy-validation
            >
    
                <v-text-field
                placeholder="Title"
                class="text-input-black"
                color="black"
                v-model="title"
                :counter="20"
                :rules="nameRules"
                label="Title"
                required
                ></v-text-field>
                 
          </v-form>
        </v-card-title>

        <v-card-text class="py-5">
         <v-textarea
              v-model="body"
              color="white"
            >
              <template v-slot:label>
                <div>
                 Body
                </div>
              </template>
            </v-textarea>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
           <v-btn
            color="primary"
            text
            @click="onSubmit"
            
          >
            Add
          </v-btn>
          <v-btn
            color="red"
            text
            @click="dialog = false"
          >
            Cancel
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
      props: {
          Title: String,
          Body: String,
      },

    data () {
      return {
        title: '',
        body: '',
        dialog: false,
        valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Title is required',
        v => (v && v.length <= 20) || 'Title must be less than 20 characters',
      ]
      }
    },

    methods: {
      onSubmit(e) {
        e.preventDefault;
        
        const newNote = {
          title: this.title,
          body: this.body
        }

        this.$emit('add-note',newNote)

        this.title = ''
        this.body = ''
        this.dialog = false
      }
    }
  }
</script>

<style>
.text-input-white .v-text-field__slot input {
   color: white !important;
}
</style>