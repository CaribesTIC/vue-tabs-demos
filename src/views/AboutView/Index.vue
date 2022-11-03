<script lang="ts" setup>
import { defineAsyncComponent, shallowRef } from 'vue'

const TabBuy = defineAsyncComponent(() => import('../../components/tabs2/TabBuy.vue'))
const TabSell = defineAsyncComponent(() => import('../../components/tabs2/TabSell.vue'))
const TabExchange = defineAsyncComponent(() => import('../../components/tabs2/TabExchange.vue'))
const TabSend = defineAsyncComponent(() => import('../../components/tabs2/TabSend.vue'))
const TabReceive = defineAsyncComponent(() => import('../../components/tabs2/TabReceive.vue'))
const TabEarn = defineAsyncComponent(() => import('../../components/tabs2/TabEarn.vue'))
const tabs = [
  { component: TabBuy, title: "Comprar" },
  { component: TabSell, title: "Vender" },
  { component: TabExchange, title: "Intercambiar" },
  { component: TabSend, title: "Enviar" },
  { component: TabReceive, title: "Recibir" },
  { component: TabEarn, title: "Ganar" }
]

const currentTab = shallowRef(tabs[0])
</script>

<template>
  <div>    
    <div class="myPanel">
      <div class="demo">
        <button
          v-for="(tab, index) in tabs"       
          :key="index"
          class="text-xs"
          :class="['tab-button', { active: currentTab === tab }]"
          @click="currentTab = tab"
        >          
          {{ tab.title }}
        </button>
        <KeepAlive>
	      <Component
	        :is="currentTab.component"
	        class="tab"	        
	      />
        </KeepAlive>
      </div>
    </div>
  </div>
</template>

<style scoped>
.demo {
  font-family: sans-serif;
  border: 0px solid #eee;
  border-radius: 2px;
  padding: 0px 0px;
  margin-top: 1em;
  margin-bottom: -1px;
  user-select: none;
  overflow-x: auto;
}
.tab-button {
  padding: 6px 10px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: 0px;
  margin-right: 0px;
}
.tab-button:hover {
  background: #e0e0e0;
}
.tab-button.active {
  @apply bg-blue-300 text-white;
}
.demo-tab {
  border: 1px solid #ccc;
  padding: 10px;
}
</style>
