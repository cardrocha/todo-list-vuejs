<script setup>
import { reactive } from 'vue';


const state = reactive({
  todos: ['Fazer compras', 'Comprar ração'],
  todoList: '',
})

function cadastraTarefa() {
  if (state.todoList.length >= 3) {
    state.todos.push(state.todoList)
    state.todoList = ''
  } else {
    alert('Digite mais caracteres!')
  }
}

function removerTarefa(todo) {
  state.todos = state.todos.filter((t) => t !== todo);
}


</script>

<template>
  <div class="container">  
    <ul>
        <div class="content">
          <h1>Minha lista de tarefas:</h1>
          <input @keyup="evento => state.todoList = evento.target.value" type="text" placeholder="Digite uma nova tarefa" :value="state.todoList">
          <button @click="cadastraTarefa" type="button">Cadastra +</button>
        </div>
      
      <li v-for="todo in state.todos">
        {{ todo }} -
        <button class="remove" @click="removerTarefa(todo)" type="button">X</button>
      </li>
    </ul>
  </div>
  
</template>

<style scoped>

.container {
  display: flex;
  justify-content: center;
  max-width: 960px;
  width: 100%;
  margin: 0 auto;
  text-align: center;
  background-image: url(https://img.freepik.com/vetores-gratis/vetor-de-design-de-papel-branco-em-branco_53876-161340.jpg?w=740&t=st=1677330487~exp=1677331087~hmac=bf0c023fd9205902607061d4e4524beee8d49abbc190aead6b9f3b94e0c10734);
}

.container ul li {
  list-style: none;
  margin-bottom: 5px;
  font-size: 18px;
  font-weight: bold;
}

.content {
  margin-bottom: 10px;
}

.content h1 {
  padding: 5px;
  background-color: #1b1b8e;
  color: #fff;
  text-align: center;
}

button {
  padding: 6px;
  background-color: #7be43f;
  border: none;
  border-bottom: 3px solid #52982a;
  border-radius: 5px;
  margin-left: 10px;
  font-weight: bold;
}

button:hover {
  background-color: #618f45;
  border-bottom: 3px solid #b6f591;
  color: #fff
}

.remove{
  padding: 5px;
  background-color: #e44f3f;
  border: none;
  border-bottom: 2px solid #98352a;
  border-radius: 5px;
  margin-left: 0;
  font-weight: bold;
}

.remove:hover {
  background-color: #8f4545;
  border-bottom: 2px solid #f59191;
  color: #fff
}

input {
  padding: 5px;
  font-weight: bold;
}
</style>
