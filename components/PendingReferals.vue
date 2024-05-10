<template>
   <div class="container lg:w-10/12 mx-auto mt-5  bg-white text-black ">
  <nav class=" text-black  flex items-center justify-between py-5">
    <div class="flex items-center">
      <button @click="closepage" class="">
       <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5 3 12m0 0 7.5-7.5M3 12h18" />
</svg>

      </button>
      <h5 class="ml-4 mb-0 text-lg text-black text-[22px] ">Pending Referrals</h5>
    </div>
  </nav>
  <div class="flex flex-col  ">
    <div class="bg-white rounded-lg border boder-gray ">
      <div class="p-4">
        <div class="flex flex-col">
          <div class="flex justify-between mb-2">
            <h6 class="text-lg font-semibold mb-0">Total Rewards</h6>
            <div class="flex items-center gap-1">
              </div>
          </div>
          <div class="flex justify-between">
            <h6 class="text-sm mb-0">Current Month-{{this.pendingReferalData.currentMonth}}*</h6>
            <h6 class="text-sm mb-0">{{this.pendingReferalData.totalReferal}}/{{this.pendingReferalData.referalInCurrentMonth}}</h6>
          </div>
        </div>
      </div>
    </div>
  </div>
    <div class="my-4 flex mx-3">
      <div class="text-2xl font-bold ">.</div>
      <div class="text-sm mt-3 ml-2">Your referral rewards details will be updated in 1 hour</div>
      
    </div>
<div class="bg-yellow-50  rounded-lg mb-4">
  <div class="p-4 flex items-center gap-2">
   <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="#FFC107" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="m11.25 11.25.041-.02a.75.75 0 0 1 1.063.852l-.708 2.836a.75.75 0 0 0 1.063.853l.041-.021M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9-3.75h.008v.008H12V8.25Z" />
</svg>

    <h6 class="text-sm mb-0 text-semibold">You will be rewarded for the first 10 successful referrals in a month</h6>
  </div>
</div>
<div>
  <div  v-for="(option, key) in this.pendingReferalData.rawards" :key="key">
<CardForPending :cardData="option"/>
</div>
   
</div>
</div>
<div class=" w-full bg-white flex items-center justify-center gap-1 py-2 text-black ">
  <h6 class="text-base mb-0">Looking for your referrals?</h6>
  <button onclick="callpage('pending_referrals.php')" class="text-base font-normal text-primary hover:underline">Referral Rewards</button>
</div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
    
    };
  },
  mounted() {
  
console.log(this.pendingReferalData,this.pendingReferalData.rewards,"this.pendingReferalData.rewards");
  },

  methods: {
   closepage(){
    this.$emit("pending-refferal-closed");
   }

 
 
  },
   props: {
    pendingReferalData: {
      type: Object,
      required: true,
    },
  
    
  },
};
</script>
<style scoped>
.container{
  width:90% !important;
}
</style>
