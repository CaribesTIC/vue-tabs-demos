<script setup lang="ts">
import { inject } from 'vue'

const { myRefThree, myFunction } = inject<{
    myRefThree: string,
    myFunction: (val: any) => void;
}>('myKeyX')

myFunction(myRefThree.value)
</script>

<template>
  <div class="demo-tab">
    <span class="text-xl font-semibold pb-8">myRefThree</span>       
  </div>
</template>
