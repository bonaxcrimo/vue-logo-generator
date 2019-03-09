<template>
  <div class="colorContainer">
    <div class="select-style">
      <select name id @change="onChangeHandler">
        <option>Select Background Color</option>
        <option value="#FFFFFF">White</option>
        <option value="#000000">Black</option>
        <option v-for="(color,index) in colors" :key="index" :value="color.option2">{{index}}</option>
      </select>
    </div>
    <div class="innerDiv">
      <Color v-for="(color,index) in colors" :key="index" :colorName="index" :options="color"/>
    </div>
  </div>
</template>
<script>
import Color from "@/components/Color";
export default {
  components: {
    Color
  },
  props: ["colors", "optionClickHandler", "backgroundChangeHandler"],
  methods: {
    onChangeHandler(e) {
      this.backgroundChangeHandler(e.target.value);
    }
  }
};
</script>
