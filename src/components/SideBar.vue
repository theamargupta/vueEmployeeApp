<script setup>
import { onBeforeMount, ref } from 'vue'

const props = defineProps({
  output: Array
})

const open = ref([props.output[0].mng.first_name])


const emit = defineEmits(['setEmployee'])
onBeforeMount(() => {
  emit('setEmployee', props.output[0].mng)
})
</script>
<template>
  <v-card>
    <v-layout>
      <v-navigation-drawer permanent theme="dark">
        <p class="px-3 py-3">Employees</p>
        <v-list nav v-model:opened="open">
          <v-list-group
            :value="employe.mng.first_name"
            v-for="employe in output"
            :key="employe.mng.id"
          >
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                :prepend-avatar="employe.mng.profile_pic"
                :title="`${employe.mng.first_name}  ${employe.mng.last_name}`"
                :subtitle="employe.mng.email"
                :value="`${employe.mng.first_name}  ${employe.mng.last_name}`"
                @click="() => emit('setEmployee', employe.mng)"
              ></v-list-item>
            </template>
            <v-list-item
              v-for="user in employe.emp"
              :key="user.id"
              :prepend-avatar="user.profile_pic"
              :title="`${user.first_name}  ${user.last_name}`"
              :subtitle="user.email"
              :value="`${user.first_name}  ${user.last_name}`"
              @click="() => emit('setEmployee', user)"
            ></v-list-item>
          </v-list-group>
        </v-list>
      </v-navigation-drawer>
      <v-main style="height: 99vh">
        <slot>Fallback content</slot>
      </v-main>
    </v-layout>
  </v-card>
</template>
