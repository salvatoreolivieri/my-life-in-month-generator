<script setup lang="ts">
import moment from "moment"
import JsPDF from "jspdf"
import html2canvas from "html2canvas"

const inputValue = ref()
const livedMonths = ref(0)

const livedMonthsMessages = computed(() =>
  livedMonths.value ? livedMonths.value : "..."
)

const calculateLivedMonths = (date: moment.MomentInput) => {
  const today = moment()
  const birthday = moment(date)
  livedMonths.value = today.diff(birthday, "months")
  // console.log(livedMonths.value)
}

const updateInputValue = (date: any) => {
  inputValue.value = date

  calculateLivedMonths(inputValue.value)
}

const generateCalendar = async () => {
  // console.log("generate")

  // Crea un nuovo oggetto JsPDF
  const doc = new JsPDF("p", "cm", "a3")

  // Seleziona l'elemento da stampare
  const element = document.getElementById("filled-calendar")

  // Utilizza html2canvas per convertire l'elemento in un'immagine
  const canvas = await html2canvas(element)
  const imgData = canvas.toDataURL("image/png")

  // Aggiungi l'immagine alla pagina del PDF
  doc.addImage(imgData, "PNG", 2.3, 5.5)
  doc.save("LifeCalendar_Generator.pdf")
}
</script>

<template>
  <div id="generate" class="py-14">
    <div class="md:h-[700px] flex items-center justify-center flex-col gap-8">
      <h1 class="text-4xl text-[#2d2d2d] md:text-5xl font-bold text-center">
        Insert your <span class="text-[#78A0CF]">Birthday</span>
      </h1>

      <p class="text-center md:max-w-[420px] text-gray-700">
        Each of us who will arrive at the end of the month will have one less
        month to live. You can choose whether
        <strong>to be aware of it</strong> and use this calendar
        <strong>consciously</strong> or you can try to
        <strong>escape death</strong>. The choice is yours.
      </p>

      <div class="flex flex-col gap-3 min-h-[400px]">
        <div class="flex md:flex-row flex-col gap-10">
          <div>
            <CreativeCalendar @onSelected="(date) => updateInputValue(date)" />
            <p
              v-if="livedMonths"
              class="text-center text-zinc-300 mt-4 text-sm"
            >
              You already lived
              <span class="text-[#78A0CF]/80">{{ livedMonthsMessages }} </span>
              /

              <span class="text-[#78A0CF]/80 animate pop">1080 </span>

              months <br />
              (based on a 90 years person)
            </p>
          </div>
          <div id="filled-calendar" class="flex justify-center w-full">
            <div class="max-w-[500px] relative">
              <div
                class="max-w-[390px] top-[50px] left-[79px] flex flex-wrap gap-[2.72px]"
              >
                <div
                  v-for="x in livedMonths"
                  class="w-2 h-2 rounded-full bg-black border border-black"
                ></div>
                <div
                  v-for="x in 1080 - livedMonths"
                  class="w-2 h-2 rounded-full border border-black"
                ></div>
              </div>
            </div>
          </div>
        </div>

        <div class="w-full flex justify-center">
          <p
            v-if="livedMonths"
            class="text-center text-zinc-300 mt-4 max-w-[450px] text-sm flex justify-center"
          >
            I suggest you to print this PDF and take a moment, every first day
            of every month, to put a new circle in this calendar and say goodbye
            to the month that no longer belongs to you.
          </p>
        </div>

        <div v-if="livedMonths" class="animate pop">
          <span
            @click="generateCalendar"
            class="animate pop text-[#78A0CF] transition hover:underline cursor-pointer flex items-center gap-2 justify-center mt-3 md:hover:translate-x-4"
          >
            Generate PDF
            <IconsArrowLong />
          </span>
        </div>
      </div>
    </div>
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
