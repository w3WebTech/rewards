<template>
  <div>
    <div
      class="p-4 mx-1 px-4 my-4 py-2 bg-white rounded-md font-sans border border-gray"
    >
      <div class="flex flex-row justify-between container">
        <div class="flex">
          <div
            class="rounded-full h-9 w-9 pt-1 text-white text-lg font-bold flex justify-center text-center bg-blue-300 mt-2"
          >
            A
          </div>
          <div class="ml-2">
            <div class="flex">
              <div>{{ this.cardData.name }}</div>
            </div>
            <div>{{ this.cardData.date }}</div>
          </div>
        </div>

        <div
          class="justify-start text-xs font-grey-300 mt-2 font-sans mx-2"
          style="color: #505050"
          @click="open = !open"
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
      <div class="my-4" v-if="this.open == true" >
<div  v-for="(option, key) in this.cardData.accountDetails" :key="key">
        <div class="my-2">
          <div class="flex">
            <div :class="option.date ? 'my-2':''">
             <div class="border rounded-full p-1 flex justify-center bg-[#E8F3EE]" >
              <div v-if="option.accountOpened == true || option.accountReadyToInvest == true ">
               <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="none" class="w-3 h-3">
  <path stroke-linecap="round" stroke-linejoin="round" d="m4.5 12.75 6 6 9-13.5" />
</svg>
</div>
<div v-else>     <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="green" class="w-3 h-3">
  <path stroke-linecap="round" stroke-linejoin="round" d="m4.5 12.75 6 6 9-13.5" />
</svg></div>
              </div>
            </div>
            <div class="px-2">
              <div class="text-sm font-semibold">{{option.accountOpened == true ? "Account Opening Started":"Account Ready to Invest"}}</div>
               <div class="text-sm ">{{option.date ? option.date :""}}</div>
            </div>
            
          </div>
          
          
        </div>
       
     </div> </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      open: false,
    };
  },
  computed: {},
  watch: {},
  mounted() {
    console.log(this.cardData, "cardfdx");
  },

  methods: {},
  props: {
    cardData: {
      type: Object,
      required: true,
    },
  },
};
</script>