<template>
  <div class="container mx-auto w-10/12 h-screen">
    <nav class="navbar navbar-dark bg-dark">
      <div class="flex justify-content-between items-center">
        <button
          type="button"
          class=""
          @click="closepage"
        >
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5 3 12m0 0 7.5-7.5M3 12h18" />
</svg>

        </button>
         <h5 class="ml-4 mb-0 text-lg text-black text-[22px] ">Referral Rewards</h5>
      </div>
    </nav>
    <div class="flex flex-col w-full">
      <div class="card  border border-gray rounded-lg ">
        <div class="card-body">
          <div class="flex flex-col">
            <div class="flex justify-between ">
              <h6 class="mb-0 text-[17px] font-semibold">Current Month</h6>
              <h6 class="mb-0   text-[17px]   font-bold">26/04/2024 to 25/05/2024</h6>
            </div>
            <div class="flex justify-between ">
              <h6 class="mb-0 text-[17px] font-semibold">New A/C Opened</h6>
              <div class="flex items-center gap-1">
                <i class="fas fa-indian-rupee-sign text-gray-500 fs-6"></i>
                <h6 class="mb-0 text-[17px] font-bold" id="new-acc-opened-count" aria-value="0">
                  {{this.referalRewardData?.newAccountOpened}} x 500
                </h6>
              </div>
            </div>
            <div class="flex justify-between ">
              <h6 class="mb-1 text-[17px] font-semibold">Life Time Reward</h6>
              <div class="flex items-center gap-1 text-[17px] font-bold">
              
                <h6 class="mb-0" id="life-time-reward-amount"> ₹  {{this.referalRewardData?.lifeTimeReward}}</h6>
              </div>
            </div>
            <div class="flex justify-between">
              <h6 class="mb-1 text-[17px] font-semibold">Total Rewards</h6>
              <div class="flex items-center gap-1 text-[17px] font-bold ">
               
                <h6 class="mb-0" id="total-life-time-reward-amount"> ₹ {{this.referalRewardData?.totalRewards}}</h6>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="my-4 flex mx-3">
      <div class="text-2xl font-bold ">.</div>
      <div class="text-sm mt-3 ml-2">Your referral rewards details will be updated in 1 hour</div>
      
    </div>
   <div class="flex justify-between bg-[#F8F9FA] py-5 px-5 rounded-md">
  <div
    class="text-sm rounded-md px-4 py-2 cursor-pointer"
    :class="{ 'bg-[#4D62C7] text-white': tabName === 'tab1', 'text-[#172B4D]': tabName !== 'tab1' }"
    @click="openTab('tab1')"
  >
    New
  </div>
  <div
    class="text-sm rounded-md px-4 py-2 cursor-pointer"
    :class="{ 'bg-[#4D62C7] text-white': tabName === 'tab2', 'text-[#172B4D]': tabName !== 'tab2' }"
    @click="openTab('tab2')"
  >
    LifeTime
  </div>
  <div
    class="text-sm rounded-md px-4 py-2 cursor-pointer"
    :class="{ 'bg-[#4D62C7] text-white': tabName === 'tab3', 'text-[#172B4D]': tabName !== 'tab3' }"
    @click="openTab('tab3')"
  >
    Withdraw
  </div>
</div>

<div>
  <div  v-show="tabName === 'tab1'">
    <div v-if="this.newRewardsCategory && this.newRewardsCategory.content.length > 0" >
<div  v-for="(option, key) in this.newRewardsCategory.content" :key="key">
<CardSection :cardData="option"/>
</div>

    </div>
    <div v-else>
      <EmptyImageTab/>
    </div>
   
  </div>
  <div  v-show="tabName === 'tab2'">
      <div v-if="this.lifeTimeRewardsCategory && this.lifeTimeRewardsCategory.content.length > 0" >
<div  v-for="(option, key) in this.lifeTimeRewardsCategory.content" :key="key">
<CardSection :cardData="option"/>
</div>

    </div>
    <div v-else>
      <EmptyImageTab/>
    </div>
  </div>
  <div   v-show="tabName === 'tab3'">
    <div v-if="this.withdrawRewardsCategory && this.withdrawRewardsCategory.content.length > 0" >
<div  v-for="(option, key) in this.withdrawRewardsCategory.content" :key="key">
<CardSection :cardData="option"/>
</div>

    </div>
    <div v-else>
      <EmptyImageTab/>
    </div>
  </div>
</div>
<div class=" w-full bg-white flex items-center justify-center gap-1 py-2">
  <h6 class="text-base mb-0">Looking for your referrals?</h6>
  <button onclick="callpage('pending_referrals.php')" class="text-base font-normal text-primary hover:underline">Pending Referrals</button>
</div>
      
 </div>
     
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
     tabName:null,
    };
  },
  mounted() {
    this.openTab('tab1');

  },

  methods: {
   openTab(tabId) {
  console.log(tabId, "tabId")
  this.tabName = tabId;
  
   
},
closepage(){
  this.$emit("refferal-rewards-closed");
}

 
 
  },
   props: {
    referalRewardData: {
      type: Object,
      required: true,
    },
   newRewardsCategory: {
      type: Object,
      required: true,
    },
    lifeTimeRewardsCategory:{
      type: Object,
      required: true,
    },
    withdrawRewardsCategory:{
      type: Object,
      required: true,
    },
    
  },
};
</script>
<style scoped>
.card-body {
  padding:15px !important;
  
}
</style>