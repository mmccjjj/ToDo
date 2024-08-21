<script setup>
import {ref} from 'vue';

const newTodoTitle= ref('')
const newTodoItem= ref('')

const todoList= ref([

{  id: 1,
  title: 'Make Todo App',
  content: 'Some instructions',
  isComplete: false
}

])

function addTodo(){
  todoList.value.push(
    {
      id: todoList.value.length + 1,
      title: newTodoTitle.value,
      content: newTodoItem.value,
      isComplete: false
    }
  )
}

function deleteTodo(index) {

  todoList.value.splice(index, 1);

  
}
</script>

<template>
  <div>
  <form @submit.prevent="$event => addTodo()">
    <input type="text" name="title" v-model="newTodoTitle" placeholder="Titel"/>
    <input type="text" name="content" v-model="newTodoItem" placeholder="Content"/>
    <button>Add Todo</button>
  </form>
  <div class="about">
    <h1>ToDo</h1>
    <div 
    v-for="(item, index) in todoList" :key= "item.id" 
    class="todo-item" 
    :class= "item.isComplete ? 'green' : 'red'">
      <h3>{{ item.title }}</h3>
      <p>{{ item.content }}</p>
      <label for="completed">
        {{ item.isComplete == false? 'ToDo': 'Done' }}
        <input type="checkbox" id="completed" v-model="item.isComplete">
      </label>
      <button @click="$event => deleteTodo(index)">Delete</button>
    </div>
  </div>
</div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

.todo-item{
  border: 0.25rem;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
  padding: 0.25rem 0.5rem;

}

.green{
  background-color: green;
}

.red{
  background-color: red;
}

</style>
