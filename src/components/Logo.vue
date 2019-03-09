<template>
  <div class="svg-container">
    <svg
      id="logo-svg"
      width="320px"
      height="221px"
      viewBox="0 0 256 221"
      version="1.1"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      preserveAspectRatio="xMidYMid"
    >
      <g>
        <path d="M0,0 L128,220.8 L256,0 L204.8,0 L128,132.48 L50.56,0 L0,0 Z" fill="#41B883"></path>
        <path
          d="M50.56,0 L128,133.12 L204.8,0 L157.44,0 L128,51.2 L97.92,0 L50.56,0 Z"
          fill="#35495E"
        ></path>
      </g>
    </svg>
    <div class="downloadLinks">
      <a id="downloadLink" class="downloadLink button">Download SVG</a>
      <a id="downloadLinkForImage" class="downloadLink button">Download Image</a>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    __setPathOne(color) {
      let logoSVG = document.getElementById("logo-svg");
      let g = logoSVG.querySelector("g");
      let paths = g.querySelectorAll("path");
      let path = paths[0];
      path.style.fill = color;
    },
    __setPathTwo(color) {
      let logoSVG = document.getElementById("logo-svg");
      let g = logoSVG.querySelector("g");
      let paths = g.querySelectorAll("path");
      let path = paths[1];
      path.style.fill = color;
    },
    __downloadSVG() {
      let logoSVG = document.getElementById("logo-svg");
      let svgData = logoSVG.outerHTML;
      let svgBlob = new Blob([svgData], {
        type: "image/svg+xml;charset=utf-8"
      });
      let svgUrl = URL.createObjectURL(svgBlob);
      let downloadLink = document.getElementById("downloadLink");
      downloadLink.href = svgUrl;
      downloadLink.download = "vue-logo.svg";
    },
    __downlaodImage() {
      let svg = document.getElementById("logo-svg");
      var svgSize = svg.getBoundingClientRect();
      var svgData = new XMLSerializer().serializeToString(svg);

      var canvas = document.createElement("canvas");
      var ctx = canvas.getContext("2d");

      var img = document.createElement("img");

      var svgSize = svg.getBoundingClientRect();
      canvas.width = svgSize.width;
      canvas.height = svgSize.height;

      img.setAttribute("src", "data:image/svg+xml;base64," + btoa(svgData));

      img.onload = function() {
        ctx.drawImage(img, 0, 0);
        var imgsrc = canvas.toDataURL("image/png");
        let a = document.getElementById("downloadLinkForImage");
        a.href = imgsrc;
        a.download = "vue-logo.png";
      };
    }
  },
  mounted() {
    let { pathOne, pathTwo } = this.svgColorObj;
    this.__setPathOne(pathOne);
    this.__setPathTwo(pathTwo);
    this.__downloadSVG();
    this.__downlaodImage();
  },
  watch: {
    svgColorObj: function(val, oldVal) {
      Object.assign(this.svgColorObj, val);
      let { pathOne, pathTwo } = this.svgColorObj;
      this.__setPathOne(pathOne);
      this.__setPathTwo(pathTwo);
      this.__downloadSVG();
      this.__downlaodImage();
    }
  },
  props: ["svgColorObj"]
};
</script>

