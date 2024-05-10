<template>
  <div v-if="this?.isReferalRewards == true" class="bg-white">
    <ReferalRewards
      :referalRewardData="this.referalRewardData"
      :newRewardsCategory="this.newRewardsCategory"
      :lifeTimeRewardsCategory="this.lifeTimeRewardsCategory"
      :withdrawRewardsCategory="this.withdrawRewardsCategory"
      @refferal-rewards-closed="closerefferalPage"
    />
  </div>
  <div v-else-if="this?.isPendingReferal == true" class="bg-white">
    <PendingReferals
      :pendingReferalData="this.pendingReferalData"
      @pending-refferal-closed="closependingPage"
    />
  </div>
  <div v-else class="bg-white">
    <div>
      <div
        class="hero container mx-auto lg:w-10/12 justify-center shadow-sm rounded-md my-2"
      >
        <div class="hero-content flex-col lg:flex-row">
          <img src="/public/voucher1.png" class="max-w-screen lg:h-[270px]" />
        </div>
      </div>

      <div
        class="container lg:w-10/12 mx-auto px-5 bg-[#F2F8FF] shadow-sm rounded-lg"
      >
        <div class="">
          <div
            class="flex justify-center items-center text-center text-[15px] font-semibold py-4"
          >
            Use below Referral Code to refer your friends to Goodwill and get
            rewarded
          </div>
        </div>
        <div class="py-3">
          <div class="flex rounded" role="group" aria-label="Basic example">
            <div
              onclick="copyText()"
              class="flex w-full items-center justify-center px-3 py-3 bg-white border-2 border-gray-800 border-dotted rounded-l-md"
            >
              <svg
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
                  d="M15.75 17.25v3.375c0 .621-.504 1.125-1.125 1.125h-9.75a1.125 1.125 0 0 1-1.125-1.125V7.875c0-.621.504-1.125 1.125-1.125H6.75a9.06 9.06 0 0 1 1.5.124m7.5 10.376h3.375c.621 0 1.125-.504 1.125-1.125V11.25c0-4.46-3.243-8.161-7.5-8.876a9.06 9.06 0 0 0-1.5-.124H9.375c-.621 0-1.125.504-1.125 1.125v3.5m7.5 10.375H9.375a1.125 1.125 0 0 1-1.125-1.125v-9.25m12 6.625v-1.875a3.375 3.375 0 0 0-3.375-3.375h-1.5a1.125 1.125 0 0 1-1.125-1.125v-1.5a3.375 3.375 0 0 0-3.375-3.375H9.75"
                />
              </svg>

              <h6 class="mb-0 ml-2">GZ10219</h6>
            </div>
            <button
              onclick="shareContent('https://gwkyc.in/cr/GZ10219')"
              type="button"
              class="flex w-[100px] items-center justify-center px-3 py-3 bg-primary text-white rounded-r-md bg-[#3E5AD9]"
            >
              <svg
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
                  d="M7.217 10.907a2.25 2.25 0 1 0 0 2.186m0-2.186c.18.324.283.696.283 1.093s-.103.77-.283 1.093m0-2.186 9.566-5.314m-9.566 7.5 9.566 5.314m0 0a2.25 2.25 0 1 0 3.935 2.186 2.25 2.25 0 0 0-3.935-2.186Zm0-12.814a2.25 2.25 0 1 0 3.933-2.185 2.25 2.25 0 0 0-3.933 2.185Z"
                />
              </svg>

              <h6 class="mb-0 ml-2">SHARE</h6>
            </button>
          </div>
        </div>

        <div class="">
          <button
            onclick="shareOnWhatsApp('https://gwkyc.in/cr/GZ10219')"
            type="button"
            class="flex items-center justify-center px-3 py-3 w-full rounded-lg bg-[#075E55] text-white hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500"
          >
            <i class="fab fa-whatsapp text-xl mr-2"></i>
            <h6 class="text-lg font-medium mb-0">SHARE LINK VIA WHATSAPP</h6>
          </button>

          <div class="p-2 py-3 text-[#6876CD] text-sm font-semibold" onclick="my_modal_2.showModal()">
            Terms And Conditions
          </div>
        </div>
      </div>

      <div class="container lg:w-10/12 mx-auto py-3">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div
            class="rounded-lg shadow-lg bg-white cursor-pointer hover:bg-gray-100"
            @click="callpage('referral_rewards')"
          >
            <div class="flex flex-col p-4">
              <div class="">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="#FFC107"
                  class="w-8 h-8 bg-[#FFF9E5] flex p-2 rounded-full shadow-md items-center justify-center text-center"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="m14.74 9-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 0 1-2.244 2.077H8.084a2.25 2.25 0 0 1-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 0 0-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 0 1 3.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 0 0-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 0 0-7.5 0"
                  />
                </svg>
              </div>

              <div class="mt-3">
                <h6 class="text-sm font-medium mb-0">Referral Rewards*</h6>
              </div>
              <div class="flex justify-between items-center mt-2">
                <h6 class="text-sm font-medium">₹0</h6>
                <span
                  class="p-1 rounded-full bg-gray-200 text-primary hover:bg-gray-300"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                    class="w-4 h-4"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      d="m8.25 4.5 7.5 7.5-7.5 7.5"
                    />
                  </svg>
                </span>
              </div>
            </div>
          </div>
          <div
            class="rounded-lg shadow-md bg-white cursor-pointer hover:bg-gray-100"
            @click="callpage('pending_referrals')"
          >
            <div class="flex flex-col p-4">
              <div class="">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="#198754"
                  class="w-8 h-8 bg-[#E7F3ED] flex p-2 rounded-full shadow-md items-center justify-center text-center"
                >
                  <path
                    fill-rule="evenodd"
                    d="M7.5 6a4.5 4.5 0 1 1 9 0 4.5 4.5 0 0 1-9 0ZM3.751 20.105a8.25 8.25 0 0 1 16.498 0 .75.75 0 0 1-.437.695A18.683 18.683 0 0 1 12 22.5c-2.786 0-5.433-.608-7.812-1.7a.75.75 0 0 1-.437-.695Z"
                    clip-rule="evenodd"
                  />
                </svg>
              </div>

              <div class="mt-3">
                <h6 class="text-sm font-medium mb-0">pendinf Refferals*</h6>
              </div>
              <div class="flex justify-between items-center mt-2">
                <h6 class="text-sm font-medium">0 invites</h6>
                <span
                  class="p-1 rounded-full bg-gray-200 text-primary hover:bg-gray-300"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                    class="w-4 h-4"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      d="m8.25 4.5 7.5 7.5-7.5 7.5"
                    />
                  </svg>
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
      
  <div class="w-10/12">
    <dialog id="my_modal_2" class="modal">
  <div class="modal-box">
    <h3 class="font-bold text-lg">Terms & Conditions</h3>
    
      <div>
        <p class="py-1" v-for="item in this?.termsAndConditions" :key="item"> {{item}} </p>
      </div>
  
  </div>
  <form method="dialog" class="modal-backdrop">
    <button>close</button>
  </form>
</dialog>
  </div>

  </div>
   
</template>
<script>
import axios from "axios";
export default defineComponent({
  setup() {},
  computed: {},

  data() {
    return {
      showBottomSheet:false,
      isTerms: false,
      isReferalRewards: false,
      isPendingReferal: false,
      referalRewardData: {
        startDate: 1715081392,
        endDate: 1715081392,
        newAccountOpened: 2,
        lifeTimeReward: 5000,
        totalRewards: 5000,
        rawards: [
          {
            title: "New",
            content: [
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
            ],
          },
          {
            title: "LifeTime",

            content: [
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
            ],
          },
          {
            title: "Withdraw",
            content: [],
          },
        ],
      },
      pendingReferalData: {
        clientCode: "GZ10219",
        currentMonth: "feb",

        date: 1715081392,
        totalReferal: 18,
        referalInCurrentMonth: 10,
        totalRewards: 5000,
        rawards: [
          {
            name: "TEST",
            date: 1715081392,
            accountDetails: [
              {
                accountOpened: true,
                date: 1715081392,
              },
              {
                accountReadyToInvest: false,
              },
            ],
          },
          {
            name: "TEST",
            date: 1715081392,
            accountDetails: [
              {
                accountOpened: true,
                date: 1715081392,
              },
              {
                accountReadyToInvest: false,
              },
            ],
          },
          {
            name: "TEST",
            date: 1715081392,
            accountDetails: [
              {
                accountOpened: true,
                date: 1715081392,
              },
              {
                accountReadyToInvest: false,
              },
            ],
          },
        ],
      },
      termsAndConditions:[
        "1. Each lead has 30 days of validity to receive rewards",
        "2. If the lead does not open UCC within the first 30 days then there would be no rewards",
        "3. The Investor should made minimum investment of Rs 5000 in Trading account",
          "4. Referrers will receive their rewards on the next working day following the receipt of a payin minimum Rs 5000 and also 1 trade by the Referral.",
          "5. 20% brokerage revenue will be shared life-time and earned brokerage will be processed on 1st of every month."
      ],
      newRewardsCategory: [],
      lifeTimeRewardsCategory: [],
      withdrawRewardsCategory: [],
    };
  },
  mounted() {
    this.separatedRewards();
  },
  methods: {
    closerefferalPage() {
      this.isReferalRewards = false;
    },
    closependingPage() {
      this.isPendingReferal = false;
    },
    callpage(pageName) {
      if (pageName == "referral_rewards") {
        this.isReferalRewards = true;
      }
      if (pageName == "pending_referrals") {
        this.isPendingReferal = true;
      }
    },
    openBottom() {
      this.isTerms = true;
    },
    separatedRewards() {
      const referalData = {
        startDate: 1715081392,
        endDate: 1715081392,
        newAccountOpened: 2,
        lifeTimeReward: 5000,
        totalRewards: 5000,
        rawards: [
          {
            title: "New",
            content: [
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
            ],
          },
          {
            title: "LifeTime",

            content: [
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
              {
                name: "Feb Life Time Withdrawal",
                status: "REWARDED",
                amount: 2000,
                referenceId: "D4RFGT54TQ45TYHFRF65",
              },
            ],
          },
          {
            title: "Withdraw",
            content: [],
          },
        ],
      };

      if (referalData && Array.isArray(referalData.rawards)) {
        this.newRewardsCategory = referalData.rawards.find(
          (reward) => reward.title === "New"
        );
        console.log(this.newRewardsCategory, "newRewardsCategory");
      } else {
        console.warn(
          "Referral data or rewards property is not defined or not an array"
        );
      }
      if (referalData && Array.isArray(referalData.rawards)) {
        this.lifeTimeRewardsCategory = referalData.rawards.find(
          (reward) => reward.title === "LifeTime"
        );
      } else {
        console.warn(
          "Referral data or rewards property is not defined or not an array"
        );
      }
      if (referalData && Array.isArray(referalData.rawards)) {
        this.withdrawRewardsCategory = referalData.rawards.find(
          (reward) => reward.title === "Withdraw"
        );
        console.log(this.withdrawRewardsCategory, "withdrawRewardsCategory");
      } else {
        console.warn(
          "Referral data or rewards property is not defined or not an array"
        );
      }
    },
  },
});
</script>
<style scoped>
.modal {
  align-items: end !important;
}
.modal-box {
  width:100% !important;
  max-width:100% !important;
  border-bottom-left-radius:0 !important;
  border-bottom-right-radius:0 !important;
  transition: all 450ms cubic-bezier(0.32,1,0.23,1) 0ms !important;
}
.container{
  width:90% !important;
}
</style>

