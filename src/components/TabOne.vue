<script setup lang="ts">
import { inject } from 'vue'

const { myRefOne, myFunction } = inject<{
    myRefOne: string,
    myFunction: (val: any) => void;
}>('myKeyX')

myFunction(myRefOne.value)
</script>

<template>
  <div class="demo-tab">
    <span class="text-xl font-semibold pb-8">myRefOne</span>       
  </div>
</template>
