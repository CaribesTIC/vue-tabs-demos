<script lang="ts" setup>
import { defineAsyncComponent, shallowRef, provide, ref } from 'vue'

const TabOne = defineAsyncComponent(() => import('../components/TabOne.vue'))
const TabTwo = defineAsyncComponent(() => import('../components/TabTwo.vue'))
const TabThree = defineAsyncComponent(() => import('../components/TabThree.vue'))

const tabs = [
  { component: TabOne, title: "TabOne" },
  { component: TabTwo, title: "TabTwo" },
  { component: TabThree, title: "TabThree" }  
]

const currentTab = shallowRef(tabs[0])

const myRefOne = ref("myRefOne")
const myRefTwo = ref("myRefTwo")
const myRefThree = ref("myRefThree")
const myFunction = (val) => console.log(val)

provide('myKeyX', {
  myRefOne,
  myRefTwo,
  myRefThree,
  myFunction
})
</script>

<template>
  <div>
    <h1 class="text-xl font-semibold">Open browser console to test the tabs...</h1>
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
