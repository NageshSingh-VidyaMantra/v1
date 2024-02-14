<template>
  <!-- <h1 class="text-3xl font-bold underline bg-red-200">Hello world!</h1> -->
  <!-- <img :src="imgpath" class="w-52" /> -->
  <div class="flex flex-col justify-center items-center px-5 py-10 gap-5">
    <div
      v-show="greenShow"
      class="p-2 px-5 bg-gradient-to-t from-lime-500 to-lime-300 rounded-lg shadow-md"
      :class="[greenHW]"
      @click="onGreenHandler"
    >
      {{ greenMessage }}
    </div>
    <div
      v-show="redShow"
      class="p-2 px-5 bg-gradient-to-t from-red-500 to-red-300 rounded-lg shadow-md"
      :class="[redHW]"
      @click="onRedHandler"
    >
      {{ redMessage }}
    </div>

    <button
      @click="
        () => {
          greenCount = 1;
          redCount = 1;
          greenShow = true;
          redShow = true;
        }
      "
    >
      reset
    </button>
  </div>
</template>

<script setup>
import { reactive, ref, watch } from "vue";
import imgpath from "../src/assets/duck.gif";
const greenCount = ref(1);
const redCount = ref(1);

const greenShow = ref(true);
const redShow = ref(true);

const greenMessage = ref("Yes");
const redMessage = ref("No");

const greenHW = ref();
const redHW = ref();

showMessage = ref(false);
displayMessage = ref("");

function onGreenHandler() {
  redCount.value = 1;
  greenCount.value += 1;
}

function onRedHandler() {
  greenCount.value = 1;
  redCount.value += 1;
}

function greenRedHW(count) {
  switch (count) {
    case 1:
      redHW.value = "min-w-[65vw]";
      greenHW.value = "min-w-[65vw]";
      break;

    case 2:
      redHW.value = "h-[12vh] w-[75vw]";
      greenHW.value = "w-[75vw]";
      break;

    case 3:
      redHW.value = "h-[50vh] w-[85vw]";
      greenHW.value = "w-[85vw]";
      break;

    case 4:
      redHW.value = "h-[80vh] w-[95vw]";
      greenHW.value = "w-[95vw]";
      break;

    default:
      break;
  }
}

watch(
  greenCount,
  (greenCount) => {
    console.log("watching green count is : ", greenCount);
    switch (greenCount) {
      case 1:
        greenRedHW(1);
        greenMessage.value = "Yes";
        break;

      case 2:
        greenRedHW(2);
        greenMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;

      case 3:
        greenRedHW(3);
        greenMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;

      case 4:
        greenRedHW(4);
        greenMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;

      default:
        greenShow.value = false;
        redShow.value = false;
        showMessage.value = true;
        displayMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;
    }
  },
  { immediate: true }
);

watch(
  redCount,
  (redCount) => {
    console.log("watching red count is : ", redCount);
    switch (redCount) {
      case 1:
        greenRedHW(1);
        redMessage.value = "No";
        break;

      case 2:
        greenRedHW(2);
        redMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;

      case 3:
        greenRedHW(3);
        redMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;

      case 4:
        greenRedHW(4);
        redMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;

      default:
        greenShow.value = false;
        redShow.value = false;
        showMessage.value = true;
        displayMessage.value =
          "abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z, abcd efdhi jkl mno pqrstu vwxy z";
        break;
    }
  },
  { immediate: true }
);
</script>