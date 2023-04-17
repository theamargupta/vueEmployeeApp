<!-- 1. State managment
ref => ref.value
reactive => reactive
 <h1>{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>

2 Attribute Bindings
v-bind => :id="title"
  <h1 :class="titleClass">Make me red</h1>

3 Event Listner
@click=@click
<button @click="increment">count is: {{ count }}</button>

4 Form Bindings
:value="text @input="onInput
v-model="text"
<input v-model="text" placeholder="Type here">

5 Conditional Rendering
v-if / v-else
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
  v-show

6 List Rendering
v-for
  <li v-for="todo in todos" :key="todo.id">
    {{ todo.text }}
  </li>

7 Computed Property
const hideCompleted = ref(false)
const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

8 Lifecycle and Template Refs
onMounted(() => {
  p.value.textContent = 'mounted!'
})

9 Watchers
watch(todoId, fetchData)

10 Components & Props
const props = defineProps({
  msg: String
})
<ChildComp :msg="greeting" />

11 Emits
<script setup>
// declare emitted events
const emit = defineEmits(['response'])

// emit with argument
emit('response', 'hello from child')
</script>
 <ChildComp @response="(msg) => childMsg = msg" />

12 Slot
<template>
  <slot>Fallback content</slot>
</template>

 -->