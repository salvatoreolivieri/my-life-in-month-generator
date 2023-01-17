<script setup lang="ts"></script>

<template>
  <div class="flex flex-col justify-center items-center py-10 md:pt-20 gap-6">
    <h1 class="md:text-7xl text-4xl text-center text-[#2D2D2D] font-bold">
      Your Life in <span class="text-[#78A0CF]">Months</span>
    </h1>

    <h4
      class="text-xl md:text-3xl max-w-[390px] md:max-w-[550px] text-gray-300 text-center"
    >
      A simple and free Life Calendar Generator to help you understand the value
      of time
    </h4>

    <!-- <button
      type="button"
      class="border border-[#78A0CF] hover:text-white hover:bg-[#78A0CF]/70 text-[#78A0CF] hover:border-[#78A0CF]/70 mb-5 font-medium rounded-lg px-5 py-2.5 shadow-md text-lg"
    >
      <a href="#generate">Generate</a>
    </button> -->

    <a
      class="font-medium text-lg text-[#78A0CF] flex flex-col gap-3 items-center relative select-none"
      href="#generate"
      >Generate a calendar like this

      <IconsFunArrow class="text-[#78A0CF] rotate-180 absolute top-[32px] right-[51px]" />
      <IconsUnderline class="text-[#78A0CF] absolute top-[26px] right-1" />
    </a>

    <div class="max-w-[500px] relative -mx-2 mt-10">
      <img
        class="w-full opacity-70"
        src="../../assets/img/how-it-work.png"
        alt=""
      />
    </div>
  </div>
</template>

<style scoped lang="scss"></style>
