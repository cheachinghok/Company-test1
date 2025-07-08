<template>
  <div class="relative inline-block text-left">
    <!-- Toggle Button -->
     <!-- bg-gradient-to-b from-[#111] to-[#444] text-yellow-300 shadow-lg font-bold-->
    <button @click="toggle()"
        class=" px-4 py-2 rounded-full w-[130px]"
        :class="isOpen?'bg-gradient-to-b from-[#111] to-[#444] text-yellow-300 shadow-lg font-bold':''"
    >
     <span >{{ title }}</span> 
    </button>

    <!-- Dropdown Menu -->
    <transition name="fade-slide">
      <div v-if="isOpen"
           class="absolute w-[130px] rounded-3xl bg-stone-300 z-10 overflow-hidden">
        <ul class="divide-gray-200">
          <li v-for="item in menuItems" :key="item.text"
              class="flex items-center justify-center gap-1 py-1 hover:bg-gray-100 transition">
              <div class="flex items-center py-2 rounded-3xl bg-[#FFFFFF1A] w-full px-1 mx-1">
                <img :src="item.icon" alt="" class="w-8 h-8 rounded-full" />
                <span class="font-semibold text-gray-800">{{ item.text }}</span>
              </div>
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script setup>

const props = defineProps({
title: {
    type: String,
    default: () => "",
},
openKey: Number,
currentKey: Number,
});
const emit = defineEmits(['update:open'])
const isOpen = computed(() => props.openKey === props.currentKey)
    function toggle() {
    emit('update:open', props.currentKey)
    }
const menuItems = [
  { text: 'BÓNG ĐÁ', icon: '/images/menu1.gif' },
  { text: 'ĐUA BI', icon: '/images/menu2.gif' },
  { text: 'BÓNG RỔ', icon: '/images/menu3.gif' },
  { text: 'E-SPORTS', icon: '/images/menu4.gif' },
  { text: 'CASINO', icon: '/images/menu5.gif' }
]
</script>

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
