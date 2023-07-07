<script lang="ts" setup>
import { Filter } from '@vicons/ionicons5'
import { NIcon } from 'naive-ui'
import type { DrawerPlacement } from 'naive-ui'
import { NDrawer, NDrawerContent } from 'naive-ui'

const activeRef = ref(false)
const placementRef = ref<DrawerPlacement>('right')
const activate = (place: DrawerPlacement) => {
  activeRef.value = true
  placementRef.value = place
}


defineProps({
  showMenu: Function
})
</script>

<template>
  <nav class="">
    <div class="flex justify-between items-center p-5 ">
      <div class="logo-container">
        <span class="text-base md:text-5xl font-black text-black">
          FM.
        </span>
      </div>
      <div class="hamburger-btn md:hidden cursor-pointer">
        <n-icon class="text-2xl text-black"
                @click="activate('right')"
        >
          <Filter />
        </n-icon>
      </div>
      <ul class="hidden md:flex md:justify-between md:w-4/6">
        <router-link to="/" class="no-underline text-2xl font-semibold text-indigo-900 opacity-50 hover:opacity-100 cursor-pointer">Home</router-link>
        <router-link to="about-us" class="no-underline text-2xl font-semibold text-indigo-900 opacity-50 hover:opacity-100 cursor-pointer">About us</router-link>
        <li class="text-indigo-900 opacity-50 hover:opacity-100 cursor-pointer">Location</li>
      </ul>
    </div>

    <n-drawer
        v-model:show="activeRef"
        :default-width="250"
        :placement="placementRef"
        resizable
    >
      <n-drawer-content>
        <div class="bg-blue-950 h-full flex items-center">
          <ul class="flex flex-col h-3/6 justify-around  list-none ">
            <li class="font-semibold text-xl text-white">Home</li>
            <li class="font-semibold text-xl text-white">New</li>
            <li class="font-semibold text-xl text-white">Popular</li>
            <li class="font-semibold text-xl text-white">Trending</li>
            <li class="font-semibold text-xl text-white">Categories</li>
          </ul>
        </div>

      </n-drawer-content>
    </n-drawer>
  </nav>
</template>

<style scoped>
ul{
  list-style: none;
}
li{
  font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
  Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
  font-size: 20px;
  font-weight: bold;
}
</style>
