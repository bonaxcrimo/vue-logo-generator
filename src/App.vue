<template>
  <div id="app">
    <Header/>
    <div class="container">
      <Logo :svgColorObj="svgColorObj"/>
      <ColorContainer
        :colors="color"
        :optionClickHandler="optionClickHandler"
        :backgroundChangeHandler="backgroundChangeHandler"
      ></ColorContainer>
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
        pathOne: "#41B883",
        pathTwo: "#35495E"
      }
    };
  },
  methods: {
    optionClickHandler(value) {
      this.svgColorObj = Object.assign(
        {},
        {
          pathOne: value
        }
      );
    },
    backgroundChangeHandler(value) {
      console.log(value);

      this.svgColorObj = Object.assign(
        {},
        {
          pathTwo: value
        }
      );
      this.$set(this.svgColorObj);
    }
  },
  components: {
    Header,
    ColorContainer,
    Logo
  }
};
</script>
