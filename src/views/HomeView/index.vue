<script lang="ts">
// @ts-nocheck
import { defineComponent, defineAsyncComponent } from 'vue'

const TabStep1 = defineAsyncComponent(() => import('../../components/tabs/TabStep1/Index.vue'))
const TabStep2 = defineAsyncComponent(() => import('../../components/tabs/TabStep2/Index.vue'))
const TabStep3 = defineAsyncComponent(() => import('../../components/tabs/TabStep3.vue'))
const TabStep4 = defineAsyncComponent(() => import('../../components/tabs/TabStep4.vue'))
const TabStep5 = defineAsyncComponent(() => import('../../components/tabs/TabStep5.vue'))
const TabStep6 = defineAsyncComponent(() => import('../../components/tabs/TabStep6.vue'))

export default defineComponent({  
  components: { TabStep1, TabStep2, TabStep3, TabStep4, TabStep5, TabStep6 },
  data() {
    return {
      currentTab: {
        name: 'Step1',
        title: 'Datos Personales'
      },      
      tabs: [
        { name: 'Step1', title: 'Datos Personales' },
        { name: 'Step2', title: 'Dirección Habitación' },
        { name: 'Step3', title: 'Datos Tasador' },
        { name: 'Step4', title: 'Datos Laborales' },
        { name: 'Step5', title: 'Vista Previa' },
        { name: 'Step6', title: 'Adjuntar Recaudos' }
      ],
      errors: {}  
    }
  },
  computed: {    
    currentTabComponent() {
      return 'tab-' + this.currentTab.name.toLowerCase()
    }   
  }
  
})
</script>

<template>

  <div>
    <AppPageHeader>Crear Nueva Solicitud</AppPageHeader>
    
    <div class="flex space-x-2">
      <AppLink class="btn btn-primary" to="/usuarios">
        Ver todas
      </AppLink>      
    </div>
    
    
    <div class="myPanel">
      <div class="timeLine">   
        <div
          v-for="(tab, index) in tabs"
          v-bind:key="index"
          v-bind:class="currentTab === tab ? 'intro-y myZIndex1' : 'intro-x myZIndex2'"
          v-on:click="currentTab = tab"          
        >          
          <button :class="currentTab.name === tab.name ? 'btnActive btn btn-primary' : 'btnInActive btn'">{{index + 1 }}</button>
          <div :class="currentTab === tab ? 'divActive' : 'divInActive'">
            {{ tab.title }}
          </div>           
        </div>
      </div>
      
      <div class="demo mx-5">        
        <keep-alive>
          <component
            v-bind:is="currentTabComponent"
            class="tab intro-y"
          ></component>
        </keep-alive>
      </div>
      
    </div>
    
    
    
    

    
      
    
  </div>  
</template>

<style scoped>


.myPanel {
  @layer intro-y;
  @layer box;
  @apply py-10 sm:py-20 mt-5;
}

.timeLine {
  @apply
    relative
    before:hidden
    before:lg:block
    before:absolute
    before:w-[69%]
    before:h-[3px]
    before:top-0
    before:bottom-0
    before:mt-4
    before:bg-slate-100
    flex
    flex-col
    lg:flex-row
    justify-center
    px-5
    sm:px-20;
}

.myZIndex1 {
  /*@layer intro-y;*/
  @apply lg:text-center flex items-center lg:block flex-1 z-10;
}

.myZIndex2 {
  /*@layer intro-x;*/
  @apply lg:text-center flex items-center mt-5 lg:mt-0 lg:block flex-1 z-10;
}

.btnActive {
  @apply w-10 h-10 rounded-full;
}

.btnInActive {
  @apply w-10 h-10 rounded-full text-slate-500 bg-slate-100;
}

.divActive {
  @apply lg:w-32 font-medium text-base lg:mt-3 ml-3 lg:mx-auto;
}

.divInActive {
  @apply lg:w-32 text-base lg:mt-3 ml-3 lg:mx-auto text-slate-600;
}

.demo {
  font-family: sans-serif;
  border: 0px solid #eee;
  border-radius: 0px;
  padding: 0px 0px;
  margin-top: 1em;
  margin-bottom: 1px;
  user-select: none;  
  @apply bg-gray-100 drop-shadow-2xl;
}

.demo-tab {
  @apply h-auto min-h-full;
  border: 0px solid #ccc;
  padding: 10px;
}
</style>
