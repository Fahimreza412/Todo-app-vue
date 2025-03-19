 <script setup>
import { ref,onMounted,computed,watch } from "vue";
const todos = ref([])
const name = ref('')

const inputContent = ref('')
const inputCategory = ref(null)

const todoAsync = computed(() => todo.value.sort((a,b) => {
  return a.createdAt - b.createdAt
}))
watch(name,(newVal) => {
  localStorage.setItem('name',newVal)
})
onMounted(()=>{
  name.value = localStorage.getItem('name') || ''
})
const addTodo = () => {}
</script>
<template>
  <!-- <h1 style="text-align: center; margin-top: 10vh;">To-Do-List</h1> -->
<main class="app">
<section class="greeting">
  <h2 class="title">
    What's up, <input type="text" placeholder="Name here" v-model="name">
  </h2>
</section>
  <section class="create-todo">
<h3>Create A Todo</h3>

<form @submit.prevent="addTodo">
  <h4>What's on your todo List?</h4>
  <input 
  type="text"
   placeholder="e.g make a video"
    v-model="inputContent" >
<!-- {{ inputContent }} -->
  <h4>Pick a category</h4>
<div class="options">
<label>
<input type="radio" 
name="category"
value="business"
v-model="inputCategory">
<span class="bubble business"></span>
<h2>Business</h2>
</label>

<label>
<input type="radio" 
name="category"
value="personal"
v-model="inputCategory">
<span class="bubble personal"></span>
<h2>Personal</h2>
</label>
<!-- {{ inputCategory }} -->
</div>
</form>
  </section>



</main>
</template> 


