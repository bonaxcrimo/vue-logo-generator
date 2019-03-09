<template>
  <div id="app">
    <Header/>
    <div class="container"></div>
    <ColorContainer :colors="color"></ColorContainer>
  </div>
</template>

<script>
import Header from "@/components/Header";
import ColorContainer from "@/components/ColorContainer";
import * as colors from "@/data/color";
export default {
  name: "App",
  data() {
    return {
      color: colors.colors
    };
  },
  components: {
    Header,
    ColorContainer
  }
};
</script>
