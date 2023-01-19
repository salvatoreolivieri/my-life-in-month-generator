<script setup lang="ts">
import moment from "moment"

const livedMonths = ref()

const livedMonthsMessages = computed(() =>
  livedMonths.value ? livedMonths.value : "..."
)

const calculateLivedMonths = (date) => {
  const today = moment()
  const birthday = moment(date)
  livedMonths.value = today.diff(birthday, "months")
  console.log(livedMonths.value)
}

const inputValue = ref()

const updateInputValue = (date) => {
  inputValue.value = date

  calculateLivedMonths(inputValue.value)
}

const generateCalendar = () => {
  console.log("generate")
}
</script>

<template>
  <div id="generate" class="py-14">
    <div class="md:h-[700px] flex items-center justify-center flex-col gap-8">
      <h1 class="text-4xl text-[#2d2d2d] md:text-5xl font-bold text-center">
        Insert your <span class="text-[#78A0CF]">Birthday</span>
      </h1>

      <p class="text-center md:max-w-[420px] text-gray-700">
        Each of us who will arrive at the end of the month and will have one
        less month to live. You can choose whether
        <strong>to be aware of it</strong> and use this calendar
        <strong>consciously</strong> or you can try to
        <strong>escape death</strong>. The choice is yours.
      </p>

      <div class="flex flex-col gap-3 min-h-[400px]">
        <CreativeCalendar @onSelected="(date) => updateInputValue(date)" />

        <div v-if="livedMonths" class="animate pop">
          <p class="text-center text-zinc-300 mt-1 text-sm">
            You already lived
            <span class="text-[#78A0CF]/80 animate pop"
              >{{ livedMonthsMessages }}
            </span>
            months
          </p>
          <span
            @click="generateCalendar"
            class="animate pop text-[#78A0CF] transition hover:underline cursor-pointer flex items-center gap-2 justify-end mt-5 md:hover:translate-x-4"
          >
            Create
            <IconsArrowLong />
          </span>
        </div>
      </div>
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

<style lang="scss" scoped>
.animate {
  animation-duration: 0.3s;
  animation-name: animate-fade;
  animation-delay: 0s;
  animation-fill-mode: backwards;
}
.pop {
  animation-name: animate-pop;
}

@keyframes animate-pop {
  0% {
    opacity: 0;
    transform: scale(0.5, 0.5);
  }

  50% {
    opacity: 0.5;
    transform: scale(0.75, 0.75);
  }
  100% {
    opacity: 1;
    transform: scale(1, 1);
  }
}
</style>
