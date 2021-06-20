<template>
  <div class="text-sm flex flex-col justify-center items-center">
    <div class="w-3/4 flex h-40 mt-3">
      <input
        type="text"
        :value="listDisplay"
        class="border border-black w-full h-full"
      />
    </div>

    <div class="mt-36 p-5 w-max bg-gray-300 rounded shadow-lg">
      <div
        class="py-0.5 gap-1 flex"
        v-for="(char, index) in characters"
        :key="char.index"
        :class="{ 'justify-center': index === 2 || 4 }"
      >
        <button
          class="bg-white h-12 inline-block p-4"
          v-for="item in char.row"
          :key="item"
          @click="btnClick(isShiftClicked ? item.alternate : item.name)"
          :class="{
            'w-12': item,
            'w-max': item.name === 'backspace',
            'w-10/12': item.name === 'spacebar',
          }"
        >
          <span v-if="isShiftClicked">{{ item.alternate }}</span>
          <span v-else>{{ item.name }}</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "customKeyboard",
  data() {
    return {
      areaDisplay: [],
      isShiftClicked: false,
      characters: [
        {
          row: [
            { name: "1", value: 1, alternate: "!" },
            { name: "2", value: 2, alternate: "'" },
            { name: "3", value: 3, alternate: "£" },
            { name: "4", value: 4, alternate: "$" },
            { name: "5", value: 5, alternate: "%" },
            { name: "6", value: 6, alternate: "^" },
            { name: "7", value: 7, alternate: "&" },
            { name: "8", value: 8, alternate: "*" },
            { name: "9", value: 9, alternate: "(" },
            { name: "0", value: 0, alternate: ")" },
          ],
        },
        {
          row: [
            { name: "q", value: "q", alternate: "Q" },
            { name: "w", value: "w", alternate: "W" },
            { name: "e", value: "e", alternate: "E" },
            { name: "r", value: "r", alternate: "R" },
            { name: "t", value: "t", alternate: "T" },
            { name: "y", value: "y", alternate: "Y" },
            { name: "u", value: "u", alternate: "U" },
            { name: "i", value: "i", alternate: "I" },
            { name: "o", value: "o", alternate: "O" },
            { name: "p", value: "p", alternate: "P" },
          ],
        },
        {
          row: [
            { name: "a", value: "a", alternate: "A" },
            { name: "s", value: "s", alternate: "S" },
            { name: "d", value: "d", alternate: "D" },
            { name: "f", value: "f", alternate: "F" },
            { name: "g", value: "g", alternate: "G" },
            { name: "h", value: "h", alternate: "H" },
            { name: "j", value: "j", alternate: "J" },
            { name: "k", value: "k", alternate: "K" },
            { name: "l", value: "l", alternate: "L" },
          ],
        },
        {
          row: [
            { name: "shift", value: "", alternate: "shift" },
            { name: "z", value: "z", alternate: "Z" },
            { name: "x", value: "x", alternate: "X" },
            { name: "c", value: "c", alternate: "C" },
            { name: "v", value: "v", alternate: "V" },
            { name: "b", value: "b", alternate: "B" },
            { name: "n", value: "n", alternate: "N" },
            { name: "m", value: "m", alternate: "M" },
            { name: "backspace", value: "backspace", alternate: "backspace" },
          ],
        },

        { row: [{ name: "spacebar", value: " ", alternate: " " }] },
      ],
    };
  },
  methods: {
    btnClick(item) {
      if (item === "backspace") {
        return this.removeEl();
      }
      if (item === "shift") {
        this.isShiftClicked = !this.isShiftClicked;
        return "";
      }
      this.areaDisplay = [...this.areaDisplay, item];
      console.log(this.areaDisplay);
    },
    removeEl() {
      let removeElement = this.areaDisplay;
      removeElement.pop();
    },
  },
  computed: {
    listDisplay() {
      return this.areaDisplay.toString().replace(/,/g, "");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
