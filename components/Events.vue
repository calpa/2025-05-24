<template>
  <div
    class="w-full mx-auto bg-gradient-to-br from-[#223061] to-[#191f36] rounded-2xl shadow-2xl p-4 flex flex-col gap-4 text-white"
  >
    <!-- 標題 -->
    <div
      class="flex items-center justify-center gap-3 text-2xl font-extrabold tracking-wider"
    >
      <span>過去兩月的精彩回顧 🔥</span>
    </div>

    <!-- 活動列表 -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div
        v-for="(event, index) in events"
        :key="index"
        class="flex flex-col items-center rounded-xl p-2 shadow-md animate-fadein opacity-0"
        :class="[getEventColor(event.date)]"
        :style="{ animationDelay: `${index * 300 + 300}ms` }"
      >
        <div class="text-2xl mb-2">{{ event.icon }}</div>
        <div class="font-semibold text-base flex-1">{{ event.title }}</div>
        <div v-if="event.desc" class="text-sm bg-white/10 px-2 py-1 mt-1">
          {{ event.desc }}
        </div>
        <div class="text-xs mt-1">{{ event.date }}</div>
      </div>
    </div>

    <!-- 底部統計 -->
    <div class="flex flex-col items-center gap-1 opacity-0 animate-fadein"
        :style="{
            animationDelay: `${events.length * 300 + 1000}ms`
        }"
    >
      <div class="flex items-center gap-2 text-lg font-bold mt-2">
        <span>🎉</span>
        <span>總計已有</span>
        <span class="text-yellow-300 text-2xl font-extrabold px-2"
          >443 位朋友</span
        >
        <span>報名參加！</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import dayjs from 'dayjs'

const events = [
  {
    icon: '⚡',
    title: '第一場《Bolt.new App 工作坊》',
    date: '2025/04/12',
  },
  {
    icon: '⚡',
    title: '第二場《Bolt.new App 工作坊》',
    date: '2025/04/26',
  },
  {
    icon: '🔥',
    title: '《用 ChatGPT + Apps Script 打造 AI 表單自動化流程》',
    desc: '企劃書 + Google Form + Google Sheet + Google Apps Script',
    date: '2025/05/17',
  },
  {
    icon: '⚡',
    title: '用 Bolt.new 教你輕鬆無痛寫屬於自己的 App',
    date: '2025/05/24',
  },
  {
    icon: '🛠️',
    title: '《Vibe Coding 實作工作坊 | 0-1 生成並部屬自己的第一個產品》',
    desc: '台中線下分享會 (No-Code Desingers X Monospace X Zeabur)',
    date: '2025/05/30',
  },
  {
    icon: '🔥',
    title: 'AI 煉金術：從靈感到落地的實作分享會',
    desc: '台北線下分享會',
    date: '2025/06/01',
  },
]

const getEventColor = (date: string) => {
  if (dayjs(date).isSame(dayjs('2025-05-24'))) {
    return 'bg-amber-400'
  }
  if (dayjs(date).isBefore(dayjs('2025-05-24'))) {
    return 'bg-blue-500/70'
  }
  return 'bg-green-500/70'
}
</script>

<style scoped>
@keyframes fadein {
  0% {
    opacity: 0;
    /* transform: translateY(1.25rem); */
  }
  100% {
    opacity: 1;
    /* transform: translateY(0); */
  }
}
.animate-fadein {
  animation: fadein 0.7s cubic-bezier(.4,0,.2,1) forwards;
}
</style>