<script setup lang="ts"></script>

<template>
  <header class="md:w-[80%] pt-2 flex justify-center m-auto items-center">
    <nav>
      <ul class="flex gap-6">
        <li>
          <a
            href="#how-it-work"
            class="font-medium text-[#2d2d2d] text-sm md:text-base hover:text-[#78A0CF]"
            >How It Works</a
          >
        </li>
        <li>
          <a
            href="#philosophy"
            class="font-medium text-sm md:text-base hover:text-[#78A0CF]"
            >Philosophy</a
          >
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped lang="scss">
.cta {
  position: relative;
  margin: auto;
  padding: 19px 22px;
  transition: all 0.2s ease;
  &:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    display: block;
    border-radius: 28px;
    background: rgba(#ee3e54, 0.5);
    width: 56px;
    height: 56px;
    transition: all 0.3s ease;
  }
  span {
    position: relative;
    font-size: 16px;
    line-height: 18px;

    vertical-align: middle;
  }
  svg {
    position: relative;
    top: 0;
    margin-left: 10px;
    fill: none;
    stroke-linecap: round;
    stroke-linejoin: round;
    stroke: #ee3e54;
    stroke-width: 2;
    transform: translateX(-5px);
    transition: all 0.3s ease;
  }
  &:hover {
    &:before {
      width: 100%;
      background: rgba(#ee3e54, 1);
    }
    svg {
      transform: translateX(0);
    }
  }
  &:active {
    transform: scale(0.96);
  }
}
</style>
