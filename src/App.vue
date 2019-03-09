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
        strokeColor: "00D8FF",
        strokeWidth: "24",
        bgColor: "#222222"
      }
    };
  },
  methods: {
    optionClickHandler(value) {
      this.svgColorObj = Object.assign(
        {},
        {
          strokeColor: value
        }
      );
    },
    backgroundChangeHandler(value) {
      console.log(value);

      this.svgColorObj = Object.assign(
        {},
        {
          bgColor: value
        }
      );
      this.$set(this.svgColorObj);
      // this.$set(this, "svgColorObj", this.svgColorObj);
      // this.$emit("svgColorObj", this.svgColorObj);
    }
  },
  // watch: {
  //   svgColorObj() {
  //     this.svgColorObj = this.svgColorObj;
  //   }
  // },
  // created() {
  //   this.backgroundChangeHandler = this.backgroundChangeHandler.bind(this);
  // },
  components: {
    Header,
    ColorContainer,
    Logo
  }
};
</script>
