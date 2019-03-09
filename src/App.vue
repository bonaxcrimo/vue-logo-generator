<template>
  <div id="app">
    <!-- <Header/> -->
    <br>
    <br>
    <Color colorName="red" :options="color"></Color>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Color from "@/components/Color";
import * as colors from "@/data/color";
export default {
  name: "App",
  data() {
    return {
      color: colors.colors.purple
    };
  },
  components: {
    Header,
    Color
  }
};
</script>
