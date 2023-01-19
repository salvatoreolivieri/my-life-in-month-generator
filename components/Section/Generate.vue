<script setup lang="ts">
import moment from "moment"

const calculateLivedMonths = (date) => {
  const today = moment()
  const birthday = moment(date)
  const differenceInMonths = today.diff(birthday, "months")
  console.log(differenceInMonths)
}

const inputValue = ref()

const updateInputValue = (date) => {
  inputValue.value = date
}

const generateCalendar = () => {
  calculateLivedMonths(inputValue.value)
}
</script>

<template>
  <div
    id="generate"
    class="py-14 flex items-center justify-center flex-col gap-8 md:h-[700px]"
  >
    <h1 class="text-4xl text-[#2d2d2d] md:text-5xl font-bold text-center">
      Insert your <span class="text-[#78A0CF]">Birthday</span>
    </h1>

    <div class="flex flex-col gap-3 min-h-[400px]">
      <CreativeCalendar @onSelected="(date) => updateInputValue(date)" />

      <span
        @click="generateCalendar"
        class="text-[#78A0CF] transition hover:underline cursor-pointer duration-200 ease-out flex items-center gap-4 justify-end mt-2"
      >
        Create
        <IconsArrowLong />
      </span>
    </div>

    <!-- <div class="md:max-w-[700px]">
      <div class="relative z-0 w-full mb-6 group h-20">
        <input
          @input="saveBirthday"
          v-maska
          v-model="inputValue"
          data-maska="## / ## / ####"
          name="floating_email"
          id="floating_email"
          class="block py-2.5 px-0 w-full text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
          placeholder=" "
          required
        />
        <label
          for="floating_email"
          class="peer-focus:font-medium absolute text-sm text-gray-500 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:left-0 peer-focus:text-[#78A0CF] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6"
          >Insert your birthday</label
        >
      </div>
    </div> -->
  </div>
</template>
