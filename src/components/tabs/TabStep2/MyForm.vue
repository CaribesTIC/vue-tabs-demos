<script setup lang="ts">
// @ts-nocheck
/* 
import { reactive } from "vue"
import type User from "../types/User"
import type Role from "../types/Role"
// import type Errors from "../types/Errors"

const props = defineProps<{
  id?: string
  user: User  
  sending: boolean
  errors: any  
}>()

const emit = defineEmits<{
  (e: 'submit', user: User, userId?: string): void
}>()

const form: User = reactive(props.user)

const submit = async () => {
  emit('submit', {
    name: form.name,
    email: form.email,
    password: form.password,
    is_admin: form.is_admin
  }, props.id)
}


const rolOptions = [
  { label: ' Admin', value: true },
  { label: ' User', value: false }  
]
*/
</script>

<template>
  <form @submit.prevent="submit" class="p-4">
    <div class="grid lg:grid-cols-3 gap-3">  
      
      <div class="block">      
        <AppSelect
            :options="[{id: 'V', name: 'V' }, {id: 'E', name: 'E' }]"          
            label="Estado"
            class="w-full text-xs py-3"   
          />
      </div>

      <div class="block">      
        <AppSelect
            :options="[{id: 'V', name: 'V' }, {id: 'E', name: 'E' }]"          
            label="Municipio"
            class="w-full text-xs py-3"   
          />
      </div>

      <div class="block">      
        <AppSelect
            :options="[{id: 'V', name: 'V' }, {id: 'E', name: 'E' }]"          
            label="Parroquia"
            class="w-full text-xs py-3"   
          />
      </div>
      
      <div class="block">      
        <AppInput          
          label="Teléfono Fijo"
          type="text"          
        />
      </div>

      <div class="block">      
        <AppInput          
          label="Teléfono Móvil"
          type="text"          
        />
      </div>

      <div class="block">      
        <AppInput          
          label="Email"
          type="text"          
        />
      </div>    
      
    </div>

      <div class="block mt-2 w-full">
        <AppTextarea
          label="Dirección"
          class="w-full"      
        />
      </div>

    <div class="mt-4 px-2 border-gray-100 flex justify-end space-x-2">
      <AppBtn
        type="submit"
        :text="sending ? 'Guardando...' : 'Guardar'"
        :isDisabled='sending'
      />
    </div>
  </form>  
</template>
