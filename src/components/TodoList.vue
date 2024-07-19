<template>
  <div class="flex justify-center items-center m-32 border-2 border-gray-300 bg-green-200 rounded-lg shadow-lg p-8 h-auto">
    <div class="flex flex-col items-center w-full">
      <div class="flex flex-row w-full mb-4">
        <input 
          type="text" 
          v-model="todo_input" 
          placeholder="Enter Todo Item" 
          class="flex-grow p-2 border rounded-l-lg focus:outline-none focus:ring-2 focus:ring-green-500"
          @keyup.enter="add_todo(todo_input)"
        >
        <button 
          @click="add_todo(todo_input)" 
          class="p-2 bg-green-500 text-white rounded-r-lg hover:bg-green-600 transition duration-300"
        >
          Add
        </button>
      </div>
      <ul class="w-full">
        <li 
          v-for="(todo, index) in todo_array" 
          :key="index" 
          class="flex justify-between items-center p-2 mb-2 bg-white border rounded shadow-sm"
        >
          <span>{{ todo }}</span>
          <button 
            @click="remove_todo(todo)" 
            class="p-1 text-red-500 hover:text-red-700 transition duration-300"
          >
            ❌
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
    name: 'TodoList',

    data() {
      return {
        todo_input: "",
        todo_array: []
      };
    },
    methods: {
      add_todo(todo_input) {
        if (todo_input.trim() !== "") {
          this.todo_array.push(todo_input);
          this.todo_input = "";
        }
      },
      remove_todo(todo_input) {
        const index = this.todo_array.indexOf(todo_input);
        if (index > -1) {
          this.todo_array.splice(index, 1);
        }
      }
    }
  }
  </script>
