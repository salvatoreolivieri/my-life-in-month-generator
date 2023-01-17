<script setup lang="ts">
import { vMaska } from "maska"

const inputValue = ref(" ")

const currentYear = new Date().getFullYear()
const currentMonth = new Date().getMonth() + 1

const birthDay = ref()
const birthMonth = ref()
const birthYear = ref()

const saveBirthday = () => {
  birthDay.value = inputValue.value.split("/")[0]
  birthMonth.value = inputValue.value.split("/")[1]
  birthYear.value = inputValue.value.split("/")[2]

  console.log("giorno", birthDay.value)
  console.log("mese", birthMonth.value)
  console.log("anno", birthYear.value)
}

const validateDay = computed(() => {})
const validateMonth = computed(() => {})
const validateYear = computed(() => {})
</script>

<template>
  <div
    id="generate"
    class="py-14 flex items-center justify-center flex-col gap-10 md:h-[700px]"
  >
    <h1 class="text-[#78A0CF] text-4xl md:text-5xl font-bold text-center">
      Generate
    </h1>

    <div class="md:max-w-[700px]">
      <div class="relative z-0 w-full mb-6 group h-20">
        <input
          @input="saveBirthday"
          v-maska
          v-model="inputValue"
          data-maska="##/##/####"
          name="floating_email"
          id="floating_email"
          class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
          placeholder=" "
          required
        />
        <label
          for="floating_email"
          class="peer-focus:font-medium absolute text-sm text-gray-500 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:left-0 peer-focus:text-[#78A0CF] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6"
          >Insert your birthday</label
        >

        <a
          v-if="inputValue.length === 10"
          class="text-[#78A0CF] transition duration-200 ease-out flex items-center gap-4 justify-end mt-2"
        >
          Create
          <IconsArrowLong />
        </a>
      </div>
    </div>
  </div>
</template>
