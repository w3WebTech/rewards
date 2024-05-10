<template>
<div >
 <div class="p-4 mx-1 px-4 my-4 py-2 bg-white  rounded-md font-sans border border-gray ">
    <div class="flex flex-row justify-between container">
        <div class="flex ">
    <div
        class="rounded-full h-9 w-9 pt-1 text-white text-lg font-bold flex justify-center text-center bg-blue-300 mt-2"
      >
        A
      </div>
      <div class="ml-2">
        <div class="flex ">
            <div>{{this.cardData.name}}</div>
            <div>  <div class="bg-green-100 text-green-500 px-1 mx-1 my-1.5 rounded-md text-[10px] flex justify-center items-center text-center">{{this.cardData.status}}</div></div>
          
        </div>
        <div> ₹ {{this.cardData.amount}}</div>
        
      </div>
        </div>
  
      <div
        class="justify-start text-xs font-grey-300 mt-2 font-sans mx-2 "
        style="color: #505050" @click="open = !open"
      >
      <div>
          <div v-if="this.open == true"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="m19.5 8.25-7.5 7.5-7.5-7.5" />
</svg>
</div>
          <div v-else><svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="m4.5 15.75 7.5-7.5 7.5 7.5"
            />
          </svg></div>
        </div>

      </div>
    </div>
    <div class="" v-if="this.open == true"> 
        <div class="flex justify-between py-4">
  <div class="flex">
            <div>
                           <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
</svg>
            </div>
            <div class="px-2">
                Ref ID
            </div>
    
        </div>
        <div>{{this.cardData.referenceId}}</div>
        </div>
      
     

    
  </div>
  </div>
  
</div>

 
  
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
     open:false,

    };
  },
  computed: {

  },
  watch: {
  
  },
  mounted() {
    console.log(this.cardData,"cardfdx");
  },

  methods: {
 
  },
props: {
    cardData: {
      type: Object,
      required: true,
    },  
  },
};
</script>