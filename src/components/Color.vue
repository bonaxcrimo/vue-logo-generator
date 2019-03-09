<template>
  <div class="colorOptions">
    <ul v-if="showOptions">
      <li
        v-for="opt in options"
        :key="opt"
        v-bind:style="{ backgroundColor: opt }"
        @click="onClickOptionHandler"
      >{{opt}}</li>
    </ul>

    <button
      class="button"
      v-bind:style="{ backgroundColor: options.option2 }"
      @click="onClickHandler"
    >{{colorName}}</button>
  </div>
</template>
<script>
import _ from "lodash";
export default {
  data() {
    return {
      showOptions: false
    };
  },
  methods: {
    onClickHandler(e) {
      e.preventDefault();
      let x = !this.showOptions;
      this.showOptions = x;
    },
    onClickOptionHandler(e) {
      let selectedColor = e.target.innerHTML;
      //   this.colorName = selectedColor;
      this.optionClickHandler(selectedColor);
    }
  },
  props: ["optionClickHandler", "colorName", "options"]
};
</script>
