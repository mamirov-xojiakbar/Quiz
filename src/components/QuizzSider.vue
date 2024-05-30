<script setup>
import { toRefs } from 'vue';
import { Icon } from '@iconify/vue';
import { ref } from 'vue'

const props = defineProps({
  modelValue: Boolean
})

const emit = defineEmits(['update:modelValue'])

const { modelValue } = toRefs(props)

const toogleSide = () => {
  emit('update:modelValue', !modelValue.value)
}

</script>


<template>
  <div :class="modelValue ? 'w-[45%]' : 'w-[65px]'" class="fixed top-0 right-0 h-screen duration-300 bg-primary ">
    <div class="flex items-center justify-between shadow-md  pr-5">
      <div>
        <button class="bg-orange-700 py-8 px-2 flex justify-center hover:bg-slate-900 hover:text-white"
          :class="!modelValue ? 'w-[65px]' : ''" @click="toogleSide">

          <Icon :class="!modelValue ? '' : 'rotate-180'" class="text-4xl" icon="iconamoon:arrow-left-2-bold" />


        </button>
      </div>

      <div class="text-3xl py-8">
        time
      </div>

      <button>chiqish</button>


    </div>

    <div class="flex justify-between text-[15px] font-semibold border-b-[1px] border-b-slate-300 mx-10 ml-[70px] my-5 pb-2">
      <p>Matematika</p>
      <p>1/10</p>
    </div>

    <div class="flex pl-[70px] justify-between pr-10">
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">1</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">2</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">3</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">4</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">5</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">6</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">7</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">8</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">9</p>
      <p class="border px-3 py-1 cursor-pointer rounded-[50%] hover:bg-black hover:text-white">10</p>
    </div>

  </div>
</template>



<style lang="scss" scoped></style>