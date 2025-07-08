
<script setup>

const itemRefs = ref([])
const indexScroll = ref(0)
const showall = ref(false);
const items = [
  {
    image: '/images/soccer3.jpg',
    icon: '/images/icon1.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'live',
    statusiCon:'/images/status3.png',
    iconClass: 'mdi mdi-basketball text-orange-500',
  },
  {
    image: '/images/soccer2.jpg',
    icon: '/images/icon2.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'cancelled',
     statusiCon:'/images/status1.png',
    iconClass: 'mdi mdi-controller text-white',
  },
  {
    image: '/images/soccer1.jpg',
    icon: '/images/icon3.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'upcoming',
    statusiCon:'/images/status2.png',
    iconClass: 'mdi mdi-soccer text-white',
  },
  {
    image: '/images/soccer3.jpg',
    icon: '/images/icon1.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'upcoming',
    statusiCon:'/images/status2.png',
    iconClass: 'mdi mdi-basketball text-orange-500',
  },
    {
    image: '/images/soccer2.jpg',
    icon: '/images/icon2.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'cancelled',
    statusiCon:'/images/status2.png',
    iconClass: 'mdi mdi-controller text-white',
  },
  {
    image: '/images/soccer1.jpg',
    icon: '/images/icon3.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'upcoming',
    statusiCon:'/images/status2.png',
    iconClass: 'mdi mdi-soccer text-white',
  },
    {
    image: '/images/soccer3.jpg',
    icon: '/images/icon1.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'live',
    statusiCon:'/images/status3.png',
    iconClass: 'mdi mdi-basketball text-orange-500',
  },
  {
    image: '/images/soccer2.jpg',
    icon: '/images/icon2.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'cancelled',
     statusiCon:'/images/status1.png',
    iconClass: 'mdi mdi-controller text-white',
  },
  {
    image: '/images/soccer1.jpg',
    icon: '/images/icon3.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'upcoming',
    statusiCon:'/images/status2.png',
    iconClass: 'mdi mdi-soccer text-white',
  },
  {
    image: '/images/soccer3.jpg',
    icon: '/images/icon1.gif',
    home:"Team A",
    away:"Team B",
    commentator: 'BLV NONAME',
    status: 'upcoming',
    statusiCon:'/images/status2.png',
    iconClass: 'mdi mdi-basketball text-orange-500',
  },
]

const scrollToIndex = (index) => {
  const el = itemRefs.value[index]
  if (el) {
    el.scrollIntoView({ behavior: 'smooth', inline: 'start', block: 'nearest' })
  }
}
const scrollIndex = (direction) => {
  if (direction) {
    indexScroll.value = indexScroll.value == 0 ? 0 :indexScroll.value - 2 ; 
  }
  else{
    indexScroll.value = indexScroll.value == 4 ? 4 :indexScroll.value + 2 ; 
  }
}
</script>


<template>
    <div>
        <div class=" mt-3 flex items-end justify-end">
            <button
                v-if="showall==false"
                @click="showall = !showall"
                class="text-black focus:outline-none"
            >
                <span class="mr-3">Xem tất cả</span>
            <span class="mdi mdi-chevron-left text-xl text-green mr-2">&gt;</span>
            </button>
            <button
                v-else
                @click="showall = !showall"
                class="text-black focus:outline-none"
            >
                <span class="mr-3">Thu gọn</span>
            <span class="mdi mdi-chevron-left text-xl text-green mr-2">&gt;</span>
            </button>
        </div>
        <div class="flex items-center justify-center w-full h-full px-2 py-9 bg-[#111] rounded-lg ">
            <div
                v-show="showall==false"
                @click="scrollIndex(true);scrollToIndex(indexScroll);console.log(indexScroll)"
                class="absolute z-20 mt-[50px] -translate-y-1/2 left-0 w-8 h-16 flex items-center justify-center bg-white rounded-l-lg shadow cursor-pointer"
            >
                <span class="mdi mdi-chevron-left text-xl text-green">&lt;</span>
            </div>
            <div
                v-show="showall==false"
                @click="scrollIndex(false);scrollToIndex(indexScroll);console.log(indexScroll)"
                class="absolute z-20 mt-[50px] -translate-y-1/2 right-0 w-8 h-16 flex items-center justify-center bg-white rounded-l-lg shadow cursor-pointer"
            >
                <span class="mdi mdi-chevron-left text-xl text-green">&gt;</span>
            </div>
            <!-- Scrollable Wrapper -->
             <!-- flex overflow-x-auto gap-3 no-scrollbar scroll-smooth px-10 -->
              <!-- flex flex-wrap gap-3 px-10 -->
            <div ref="scrollWrapper" :class="[
                'flex gap-3 px-10',
                showall ? 'flex-wrap' : 'overflow-x-auto no-scrollbar scroll-smooth'
            ]">

            <!-- Cards -->
            <div
                v-for="(item, index) in items"
                :key="index"
                :ref="el => itemRefs[index] = el"
                class="relative shrink-0 w-[259px] rounded-xl overflow-hidden border border-yellow-400 bg-black shadow-lg"
            >
            
                <div
                class="absolute top-0 right-0 text-white text-xs rounded-bl-md font-bold z-10"
                >
                <img src="/images/background1.png" alt="">
                </div>
                <!-- HOT Tag -->
                <div
                class="absolute top-0 right-0 text-white text-xs px-2 py-4 rounded-bl-md font-bold z-10"
                >
                <img src="/images/Hot.png" alt="">
                </div>
                <!-- Thumbnail Image -->
                <div class="w-220 h-60 overflow-hidden ">
                    <img
                        :src="item.image"
                        alt="cover"
                        class="object-cover w-full h-full"
                    />
                    <div
                        class="absolute bottom-0 left-0 text-white text-xl"
                    >
                        <img 
                            width="34"
                            :src="item.icon"
                            alt="Icons"
                            class="ml-2 mb-1"
                        />
                        <!-- Match Info -->
                        <div class="flex w-[265px] h-13 pl-5 pr-1 bg-gradient-to-b from-[#F8E889] to-[#E4B764] rounded-xl">
                            <div>
                                <div class="flex mb-1 pl-5 pt-1">
                                <p class="text-sm text-[#b3b3b3]">{{ item.home }} <span class=" font-semibold text-[10px] text-black">VS </span>{{ item.away }}</p> 
                                </div>
                                <div class="text-sm font-bold text-black pl-8">
                                    {{ item.commentator }}
                                </div>
                            </div>
                            <!-- Status Button -->
                            <div class=" flex items-center ml-auto">
                                <div
                                v-if="item.status === 'live'"
                                >
                                <img :src="item.statusiCon" alt="Live">
                                </div>
                                <div
                                v-else-if="item.status === 'cancelled'"
                                class=""
                                >
                                <img width="45" :src="item.statusiCon" alt="notifi">
                                </div>
                                <div
                                v-else
                                class=""
                                >
                                <img width="45" :src="item.statusiCon" alt="notifi">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<style scoped>
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>