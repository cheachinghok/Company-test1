

<script setup>
// Make sure you import MDI icons if you use them
const darkMode = ref(false);
const isOpen = ref(false);
const isOpens = ref(false);
const coin = ref(false);
const openKey = ref(null)

const menuItems = [
  { text: 'Trung tâm Tài khoản', icon: '/images/person.png' },
  { text: 'Trang cá nhân', icon: '/images/home.png' },
  { text: 'Nhiệm vụ', icon: '/images/nhiem.png' },
  { text: 'Ví của bạn', icon: '/images/wallet.png' },
  { text: 'lịch sử giao dịch', icon: '/images/chart.png' },
  { text: 'Thoát tài khoản', icon: '/images/logout.png' }
]
const coinsItems = [
  { text: '20.000', icon: '/images/kingcoin.png' },
  { text: '20.000', icon: '/images/silivercoin.png' },
]
function setOpenKey(key) {
  openKey.value = openKey.value === key ? null : key
}
const toggle = () => {
  darkMode.value = !darkMode.value
}
</script>

<template>
  <header class="flex bg-red text-white w-full">
    <!-- Top gradient bar -->
     <!-- Logo -->
    <div class="absolute w-[25%] text-[82px] font-seimbold text-white rounded-tr-[50px] bg-black">
      <span class="flex justify-end pr-3">LOGO</span>
    </div>
     <div class="pl-[22%] w-full">
      <div class="pl-[5%] bg-gradient-to-r from-[#F8E889] to-[#E4B764] px-5 py-1 flex items-center text-black">
        
        <!-- Navigation Links -->
        <div class="flex gap-1 uppercase text-sm font-semibold">
          <dropdown title="Lịch Trực Tiếp" :openKey="openKey" currentKey="1" @update:open="setOpenKey" />
          <dropdown title="Lịch Thi Đấu" :openKey="openKey" currentKey="2" @update:open="setOpenKey" />
          <dropdown title="Tỷ Lệ Kèo" :openKey="openKey" currentKey="3" @update:open="setOpenKey" />
          <dropdown title="Kết Quả" :openKey="openKey" currentKey="4" @update:open="setOpenKey" />
          <dropdown title="Phòng Chat" :openKey="openKey" currentKey="5" @update:open="setOpenKey" />
          <dropdown title="Tin Tức" :openKey="openKey" currentKey="6" @update:open="setOpenKey" />
        </div>

        <!-- Right Side -->
        <div class="items-center gap-3 ml-24">
          <div class="ml-20 text-xs text-black">Xin chào, <span class="">NguyenVanDen</span></div>
          <div class="flex items-center gap-3 bg-gradient-to-r from-[#5C5C5C] to-[#000000] pl-2 pr-14 py-2 rounded-3xl">
            <!-- Coin balance -->
            <div class="flex items-center bg-white text-black px-3 py-1 rounded-full" @click="coin = !coin; isOpens = false">
               <img src="/images/coin.png" class="w-5 h-5 mr-2" />
              <span class="font-bold">1000</span>
              <div class="ml-9 w-[20px] h-[20px] bg-gradient-to-b from-[#F8E889] to-[#E4B764] border-2 border-[#F8E889] rounded-xl flex items-center justify-center bg-green-500">
                <span class="font-bold mb-[4px]">+</span>
              </div>
            </div>
              <transition name="fade-slide" class="top-16 right-30">
              <div v-if="coin"
                  class="absolute w-[151px] rounded-3xl bg-zinc-300/90 z-10 overflow-hidden">
                <ul class="pb-2">
                  <li v-for="item in coinsItems" :key="item.text"
                      class="flex items-center justify-center gap-1 py-1 hover:bg-gray-100 transition">
                      <div class="flex items-center py-2 rounded-3xl bg-[#0000001A]/10 w-full px-1 mx-1">
                        <img :src="item.icon" alt="" class="w-8 h-8 rounded-full" />
                        <span class="font-semibold text-gray-800">{{ item.text }}</span>
                      </div>
                  </li>
                  <li class="flex items-center mt-1">
                    <div class="ml-9 w-[20px] h-[20px] bg-gradient-to-b from-[#F8E889] to-[#E4B764] rounded-xl flex items-center justify-center">
                      <span class="font-bold mb-[3px]">+</span>
                    </div>
                    <span class="text-[#FFFFFF] text-sm">Nạp thêm</span>
                  </li>
                </ul>
              </div>
              
            </transition>
            <!-- Notifications -->
            <div class="relative">
              <img src="/images/noti.png" class="w-6 h-6" />
              <span class="absolute -top-2 -right-2 text-xs bg-gradient-to-b from-[#FF6761] to-[#FF1D1D] text-[#F8E889] rounded-full px-1">10</span>
            </div>

            <!-- Mail -->
            <div class="relative">
              <img src="/images/inbox.png" class="w-6 h-4" />
              <span class="absolute -top-3 -right-1 text-xs bg-gradient-to-b from-[#FF6761] to-[#FF1D1D] text-[#F8E889] rounded-full px-1">2</span>
            </div>
            <div class="relative">
              <img src="/images/calendat.png" class="w-6 h-6" />
              <!-- <span class="absolute -top-2 -right-1 text-xs bg-gradient-to-b from-[#FF6761] to-[#FF1D1D] text-[#F8E889] rounded-full px-1">2</span> -->
            </div>
          </div>

          <!-- Avatar -->
          <div class="relative -top-8"  ref="menu">
            <div class="absolute -top-3 right-1">
              <img src="/images/pro.png" class="w-10 h-10" />
            </div>
              <div class="absolute -top-5 -right-1" @click="isOpens = !isOpens ; coin = false">
                <img src="/images/border.png" alt="" class="w-14" />
              </div>
            </div>
                <!-- Dropdown with Transition -->
                <transition name="fade-slide" class="top-18 right-60">
                <div v-if="isOpens"
                    class="absolute w-64 rounded-3xl bg-gradient-to-b from-[#dcd4b4] to-white shadow-xl z-10 overflow-hidden">
                  <ul class="divide-y divide-gray-200">
                    <li v-for="(item, index) in menuItems" :key="index"
                        class=" items-center gap-3 px-2 py-1 hover:bg-gray-100 transition bg-[#FFFFFF1A]">
                        <div class="flex py-2 px-3 rounded-3xl" :class="index==0?' bg-gradient-to-b from-[#5C5C5C] to-[#000000]':''">
                          <img :src="item.icon" alt="" class="w-6 h-6 mr-5" />
                          <span :class="index==0?'text-[#F8E889] font-semibold':'text-[#5C5C5C]'">{{ item.text }}</span>
                        </div>
                    </li>
                  </ul>
                </div>
              </transition>
        </div>
      </div>

      <!-- Bottom gold nav icons -->
      <div class=" pl-[6%] bg-black px-5 py-2 flex gap-14 items-center text-[#F8E889]">
        <div class="flex items-center gap-1">
          <img width="19" src="/images/message.png" alt=""> Bảng Tin
        </div>
        <div class="flex items-center gap-1">
          <img width="19" src="/images/video.png" alt=""> Reels
        </div>
        <div class="flex items-center gap-1">
          <img width="19" src="/images/highlight.png" alt=""> Highlight
        </div>
        <div class="flex items-center gap-1">
          <img width="19" src="/images/tip.png" alt=""> Tip Kèo
        </div>
        <div class="flex items-center gap-1">
          <img width="19" src="/images/phim.png" alt=""> Phim Ảnh
        </div>
        <div class="flex items-center gap-1">
          <img width="19" src="/images/book.png" alt=""> Truyện Tranh
        </div>

        <div class="flex items-center gap-28 ml-6">
          <button class="bg-white text-black pl-1 pr-6 py-1 rounded-full text-sm font-semibold flex items-center">
            <img width="25" src="/images/Language_VN.png" alt="">
            <span>Tiếng Việt</span>
          </button>
            <button
              @click="toggle"
              class="w-[75px] h-[35px] rounded-full flex items-center transition-colors duration-300 border-2 border-[#F8E889]"
              :class="darkMode ? 'bg-gradient-to-r from-gray-800 to-black' : 'bg-gradient-to-r from-[#5C5C5C] to-[#000000] '"
            > 
              <div
                class="w-[34px] h-[30px] rounded-full flex items-center justify-center transition-all duration-500"
                :class="[
                  darkMode ? 'translate-x-[40px] bg-black text-yellow-300' : 'translate-x-0 bg-[#000000] text-yellow-800',
                  'shadow-lg'
                ]"
              >
                <span><img src="/images/switch.png" alt=""></span>
              </div>
            </button>
        </div>
          
      </div>
    </div>
  </header>
</template>

<style scoped>
.fade-slide-enter-active, .fade-slide-leave-active {
  transition: all 0.3s ease;
}
.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(-10px);
}
.fade-slide-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.fade-slide-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>