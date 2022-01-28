<template>
     <v-row>
        <v-col class="notes">
            <div :key="note.id" v-for="note in notes">
                    <Note @delete-note = "$emit('delete-note', note.id)" :note="note"/>
            </div>
        </v-col>
 </v-row>
    


</template>

<script>
import Note from "./Note";

export default {
    name: 'Notes',
    props: {
        notes: Array
    },
    components: {
        Note
    }
}
</script>

<style scoped>
.notes {
    display: flex;
    flex-wrap: wrap;
    flex-basis: auto;
}
</style>
