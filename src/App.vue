<template>
  <div id="app" class="mt-14 text-center">
    <div class="bg-red-300">
      <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
        <div class="">
          <h2
            class="
              text-3xl
              font-extrabold
              tracking-tight
              text-gray-900
              sm:text-4xl
            "
          >
            <span>Ready to dive in?</span><br />
            <span class="text-indigo-600">Start your free trial today.</span>
          </h2>
        </div>
        <div class="mt-8">
          <div class="px-1.5 inline">
            <button
              class="
                relative
                px-5
                py-3
                text-base
                font-medium
                rounded-md
                text-white
                bg-indigo-600
                hover:bg-indigo-700
              "
              @click="getData"
              v-bind:class="{ 'pr-8 pl-4 pointer-events-none': getClick }"
            >
              {{ Get
              }}<span
                class="
                  absolute
                  inline-block
                  w-4
                  h-4
                  border-2 border-red-700 border-t-0
                  ml-1
                  mt-0.5
                  rounded-full
                  animate-spin
                  opacity-0
                "
                v-bind:class="{ 'opacity-100': getClick }"
              ></span>
            </button>
          </div>
          <div class="px-1.5 inline">
            <button
              class="
                px-5
                py-3
                text-base
                font-medium
                rounded-md
                text-indigo-500
                bg-gray-200
                hover:bg-gray-300
              "
              @click="getDelete"
            >
              {{ Delete }}
            </button>
          </div>
        </div>
        <div class="mt-5">{{ apiData }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  // name: 'App',
  // el:'#app',
  data() {
    return {
      apiData: '',
      Get: '取得資料',
      Delete: '清除',
      Send: '送出資料',
      getClick: false,
    };
  },
  methods: {
    getData() {
      this.Get = '送出中...';
      this.getClick = true;
      axios.get('https://reqres.in/api/users?delay=3').then((response) => {
        this.apiData = response.data.data;
      });
      setTimeout(() => {
        this.Get = '已送出!!';
        this.getClick = false;
      }, 3000);
    },
    getDelete() {
      this.apiData = '';
      this.Get = '取得資料';
    },
  },
};
</script>
