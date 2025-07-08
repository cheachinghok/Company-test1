<template>
  <Swiper
    :slides-per-view="1.2"
    :space-between="10"
    :navigation="true"
    :breakpoints="{
      640: { slidesPerView: 2 },
      1024: { slidesPerView: 5 }
    }"
    class="mySwiper"
  >
    <SwiperSlide v-for="(match, index) in matches" :key="index">
      <div class="rounded-xl overflow-hidden bg-black text-white shadow">
        <div class="relative">
          <img :src="match.image" class="w-full h-40 object-cover" />
          <span v-if="match.hot" class="absolute top-2 right-2 bg-red-600 text-xs px-2 py-1 rounded">HOT</span>
        </div>
        <div class="p-2 text-sm">
          <p class="font-semibold">{{ match.title }}</p>
          <p class="text-yellow-400 text-xs">{{ match.broadcaster }}</p>
          <div class="flex justify-between items-center mt-1 text-xs">
            <span>{{ match.status }}</span>
            <button class="bg-yellow-400 text-black px-2 py-1 rounded text-xs">
              {{ match.button }}
            </button>
          </div>
        </div>
      </div>
    </SwiperSlide>

    <!-- Custom Arrows -->
    <template #navigation>
      <div class="swiper-button-prev text-white"></div>
      <div class="swiper-button-next text-white"></div>
    </template>
  </Swiper>
</template>

<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
import 'swiper/css/navigation'

const matches = [
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'LIVE',
    button: 'Xem ngay',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Hủy lịch',
    button: 'Xem lại',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Đặt lịch',
    button: 'Nhắc lịch',
    hot: false,
  },
    {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'LIVE',
    button: 'Xem ngay',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Hủy lịch',
    button: 'Xem lại',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Đặt lịch',
    button: 'Nhắc lịch',
    hot: false,
  },
    {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'LIVE',
    button: 'Xem ngay',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Hủy lịch',
    button: 'Xem lại',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Đặt lịch',
    button: 'Nhắc lịch',
    hot: false,
  },
    {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'LIVE',
    button: 'Xem ngay',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Hủy lịch',
    button: 'Xem lại',
    hot: true,
  },
  {
    image: '/images/soccer1.jpg',
    title: 'Team A vs Team B',
    broadcaster: 'BLV NONAME',
    status: 'Đặt lịch',
    button: 'Nhắc lịch',
    hot: false,
  }
]

const slideNext = () => {
  swiperRef.value?.slideNext()
}

const slidePrev = () => {
  swiperRef.value?.slidePrev()
}
</script>

<style scoped>
.swiper-button-prev,
.swiper-button-next {
  color: #000;
}
</style>
