<template>
  <div id="app" class="min-h-screen flex flex-col items-center justify-center bg-gray-100">
    <h1 class="text-4xl font-bold text-gray-800 mb-6">Vue.js To-Do List</h1>
    <div class="w-full max-w-md">
      <input 
        v-model="newTodo" 
        @keyup.enter="addTodo" 
        placeholder="Add a new to-do" 
        class="w-full p-2 mb-4 border rounded shadow focus:outline-none focus:ring-2 focus:ring-blue-400"
      />
      <ul class="space-y-2">
        <li 
          v-for="(todo, index) in todos" 
          :key="index" 
          class="flex items-center justify-between p-2 bg-white rounded shadow"
        >
          <div class="flex items-center">
            <input 
              type="checkbox" 
              v-model="todo.completed" 
              class="mr-2"
            />
            <span :class="{ 'line-through text-gray-500': todo.completed }">
              {{ todo.text }}
            </span>
          </div>
          <button 
            @click="removeTodo(index)" 
            class="text-red-500 hover:text-red-700"
          >
            Remove
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  data(){
    return{
      newTodo:'',
      todos:[],
    };
  },
  methods:{
    addTodo(){
      if(this.newTodo.trim()){
        this.todos.push({
          text:this.newTodo, completed:false
        });
        this.newTodo='';
      }
    },
    removeTodo(index){
      this.todos.splice(index,1);
    }
  },
  name: 'App',
  // components: {
  //   // HelloWorld
  // }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

.completed {
  text-decoration: line-through;
}
</style>
