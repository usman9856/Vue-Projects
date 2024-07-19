<template>
    <div class="flex items-center justify-center h-screen flex-col">
      <h1 class="my-20 text-3xl font-serif gradient-text">
        This a Test App for Learning only Construction
      </h1>
      <div v-if="!activeComponent" class="flex space-x-4">
        <div
          class="w-32 h-32 bg-slate-500 border-2 rounded-md cursor-pointer flex items-center justify-center"
          @click="showComponent('todoList')"
        >
          <p class="text-center text-white">Todo List</p>
        </div>
        <div
          class="w-32 h-32 bg-slate-500 border-2 rounded-md cursor-pointer flex items-center justify-center"
          @click="showComponent('countDown')"
        >
          <p class="text-center text-white">Count Down</p>
        </div>
      </div>
      <div v-else>
        <div class="my-10">
          <button class="bg-blue-600 border-2 px-5 py-2 text-white rounded-lg" @click="removeComponent()">Back</button>
        </div>
        <div>
          <TodoList v-if="activeComponent === 'todoList'" />
          <CountDown v-if="activeComponent === 'countDown'" />
        </div>
      </div>
    </div>
  </template>



<script>
import CountDown from './CountDown.vue';
import TodoList from './TodoList.vue';

export default {
    name: 'HomePage',
    components: {
        TodoList,
        CountDown
    },
    data() {
        return {
            activeComponent: null,
        };
    },
    methods: {
        showComponent(component) {
            this.activeComponent = component;
        },
        removeComponent() {
            this.activeComponent = null;
        },
    },
};
</script>



<style>
.gradient-text {
  background: linear-gradient(90deg, #ff0000, #00ff00, #0000ff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradientAnimation 3s infinite;
  background-size: 300% 300%;
}

@keyframes gradientAnimation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
</style>