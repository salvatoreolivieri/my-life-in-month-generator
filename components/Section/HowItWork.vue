<script setup lang="ts"></script>

<template>
  <div
    id="how-it-work"
    class="py-10 flex items-center justify-center flex-col gap-10"
  >
    <h1 class="text-[#2d2d2d] text-4xl md:text-5xl font-bold">
      How It <span class="text-[#78A0CF]">Works</span>
    </h1>

    <div class="flex justify-center flex-col md:flex-row gap-5 flex-wrap">
      <div
        class="block max-w-xs p-6 bg-white border border-gray-100 rounded-lg shadow-md flex-shrink-0"
      >
        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900">
          Start from the beginning
        </h5>
        <p class="font-normal text-gray-700">
          It's easy. You just insert your birthday. (do you remember it, right?)
        </p>
      </div>
      <div
        class="block max-w-xs p-6 bg-white border border-gray-100 rounded-lg shadow-md flex-shrink-0"
      >
        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900">
          Calm before the storm
        </h5>
        <p class="font-normal text-gray-700">
          We will automatically calculate the month you have lived and prepare
          for you a table that represent it.
        </p>
      </div>
      <div
        class="block max-w-xs p-6 bg-white border border-gray-100 rounded-lg shadow-md flex-shrink-0"
      >
        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900">
          Existential crisis
        </h5>
        <p class="font-normal text-gray-700">
          You see the the representation of your life in months. At first you
          cry and despair, then you became aware and you start value you time.
        </p>
      </div>
    </div>

    <a
      class="font-medium hover:underline text-lg text-[#78A0CF] flex flex-col gap-3 items-center"
      href="#philosophy"
      >Explore the Philosophy

      <IconsArrowDown class="text-[#78A0CF]" />
    </a>
  </div>
</template>

<style scoped lang="scss"></style>
