<script setup>
const props = defineProps({
  title: String,
  avatar: String,
  bio: String,
  address: String,
  email: String,
  gender: String,
  id: Number
})
const emit = defineEmits(['deleteEmployee'])
</script>
<template>
  <v-card prepend-icon="mdi-twitter" :title="props.title" class="h-screen">
    <template v-slot:prepend>
      <v-avatar color="grey-darken-3" :image="props.avatar"></v-avatar>
    </template>
    <v-card-text class="py-2"> Address: {{ props.address }} </v-card-text>
    <v-card-text class="py-2"> Bio: {{ props.bio }} </v-card-text>
    <v-card-text class="py-2"> Email: {{ props.email }} </v-card-text>
    <v-card-text class="py-2"> Gender: {{ props.gender }} </v-card-text>
    <v-card-actions>
      <v-list-item class="w-100">
        <template v-slot:append>
          <div className="justify-self-end">
            <v-btn @click="emit('deleteEmployee', props.id)">Delete</v-btn>
          </div>
        </template>
      </v-list-item>
    </v-card-actions>
  </v-card>
</template>
