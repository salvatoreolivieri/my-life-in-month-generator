<script setup lang="ts">
import Datepicker from "@vuepic/vue-datepicker"
import "@vuepic/vue-datepicker/dist/main.css"

const format = (date: any) => {
  let day = date.getDate()

  if (day < 10) {
    day = "0" + day
  }

  let month = date.getMonth() + 1
  if (month < 10) {
    month = "0" + month
  }

  const year = date.getFullYear()
  return `${day}/${month}/${year}`
}

const emit = defineEmits<{ (e: "onSelected", value: string): void }>()

const handleDate = (date: any) => {
  console.log(date)

  emit("onSelected", format(date))
}

const dateRef = Date.now()
</script>

<template>
  <div>
    <Datepicker
      class="date_picker-wrapper"
      v-model="dateRef"
      inline
      auto-apply
      reverse-years
      :max-date="new Date()"
      format="dd/mm/yyyy"
      :year-range="[1901, 2023]"
      :month-change-on-scroll="false"
      @update:modelValue="handleDate"
      @internal-model-change="handleDate"

    >
      <template #year="{ year }">
        <p>{{ year }}</p>
      </template>

      <template #calendar-icon>
        <div class="flex w-full items-center gap-1 px-2 py-2">
          <span
            class="cursor-pointer flex gap-2 items-center text-[#78A0CF] hover:underline"
          >
            <IconsClose /> Close
          </span>
        </div>
      </template>
    </Datepicker>
  </div>
</template>

<style lang="scss">
.date_picker-wrapper {
  @apply relative;
  .dp__menu {
    @apply overflow-hidden rounded-xl border-none  focus:border-none;

    box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.08);

    .dp__month_year {
      &-row {
        @apply bg-white py-2;
      }

      &_wrap {
        @apply justify-center gap-2;
      }

      // month and year selector
      &_select {
        @apply w-max text-[#78A0CF] hover:bg-transparent hover:text-[#78A0CF] hover:underline;
      }

      // lateral arrow
      &_col_nav {
        @apply hidden;
      }
    }

    .dp__calendar {
      &_wrap {
        @apply bg-zinc-50 border-t border-t-zinc-100;
      }

      // header from monday to sunday
      &_header {
        @apply gap-3 px-3 py-2;

        &_separator {
          @apply hidden;
        }

        &_item {
          @apply h-full w-[30px] flex-1 p-0;
        }
      }

      // all days
      &_row {
        @apply gap-3 py-1 px-3;
      }

      &_item {
        @apply flex items-center;

        .dp__cell_inner {
          @apply h-[30px] w-[30px] rounded-full p-0 leading-none;
        }

        .dp__today {
          @apply border-none;
        }

        .dp__active_date {
          @apply border-none bg-[#78A0CF] text-white;
        }

        .dp__date_hover {
          @apply hover:bg-[#78A0CF]/50;
        }
      }
    }

    // months selector
    .dp__overlay {
      @apply mb-[44px] bg-zinc-100 pt-[44px] text-end;

      &_container {
        @apply flex flex-col gap-2;
      }

      &_row {
        @apply gap-4 px-4;
      }

      &_col {
        @apply h-[30px] w-max flex-1 rounded-md bg-white p-0;
      }

      &_cell {
        @apply flex h-full items-center justify-center border border-zinc-200 bg-white py-0 text-gray-600 hover:bg-[#78A0CF]/20;

        &_disabled {
          @apply opacity-30 hover:bg-white/30;
        }

        &_active {
          @apply flex h-full items-center justify-center border bg-[#78A0CF]/50 text-gray-600;
        }
      }
    }

    // day selector
    .dp__instance_calendar {
      .dp__button:not(.dp__overlay_action) {
        @apply hidden hover:bg-white;
      }
    }

    .dp__overlay_action {
      @apply absolute top-0 left-0 z-50 bg-white;
    }

    .dp__now_wrap {
      @apply p-0;
    }
  }
}
</style>
