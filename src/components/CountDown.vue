
<template>
    <div class="w-full h-[100%] flex items-center justify-center flex-col">
      <p class="border-2 w-64 h-32 flex items-center justify-center text-5xl font-serif">{{ formattedTime }}</p>
      <button @click ="startTimer"  class="m-10 bg-green-500 border-2  px-5 py-3 rounded-xl">Start</button>
    </div>
  </template>

<script >
export default {
    name: 'CountDown',
    data() {
      return {
        hours: '00',
        minutes: '00',
        seconds: '00',
      };
    },
    computed: {
      formattedTime() {
        return `${this.hours}:${this.minutes}:${this.seconds}`;
      },
    },
    methods: {
      getTime() {
        const now = new Date();
        this.hours = String(now.getHours()).padStart(2, '0');
        this.minutes = String(now.getMinutes()).padStart(2, '0');
        this.seconds = String(now.getSeconds()).padStart(2, '0');
      },
      startTimer() {
        if (this.timer) {
          clearInterval(this.timer);
        }
        this.getTime();
        this.timer = setInterval(this.getTime, 1000);
      },
    },
    beforeDestroy() {
      if (this.timer) {
        clearInterval(this.timer);
      }
    },
    
  };
  </script>