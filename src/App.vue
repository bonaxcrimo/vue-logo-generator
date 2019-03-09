<template>
  <div id="app">
    <Header/>
    <div class="container">
      <Logo :svgColorObj="svgColorObj"/>
      <ColorContainer :colors="color"></ColorContainer>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Logo from "@/components/Logo";
import ColorContainer from "@/components/ColorContainer";
import * as colors from "@/data/color";
export default {
  name: "App",
  data() {
    return {
      color: colors.colors,
      svgColorObj: {
        strokeColor: "00D8FF",
        strokeWidth: "24",
        bgColor: "#222222"
      }
    };
  },
  components: {
    Header,
    ColorContainer,
    Logo
  }
};
</script>
