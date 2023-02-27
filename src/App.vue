<template>
  <div class="grid h-screen place-items-center">
    <form class=" w-2/4 h-2/4 grid place-items-center bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class="mb-4">
        <label class="block text-xl text-center text-gray-700 text-sm font-bold mb-2" for="username">
          URL
        </label>
        <input v-model="this.url" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text">
      </div>
      <div class="flex items-center justify-center">
        <button @click.prevent="submitUrl" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
          Sign In
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      url: '',
    }
  },
  methods:{
    async submitUrl(){
      const data = {
        url: this.url
      }
      await axios
          .post('https://parserali.me/scrape/', data)
          .then(response =>{
            console.log(response.data)
          })
          .catch(error =>{
            console.log(error)
          })
    }
  }
}
</script>



<style scoped>

</style>
