<template>
  <div>
    <!-- <p class="fig text-sm inline">👋 Dynamic</p>
    <span class="h[28px] bg-black p-2"
      ><span class="text-white figbold">QR</span>
      <span class="text-white fig">Codes</span></span
    >
    <p class="inline">Branded</p> -->
    <!-- <div class="flex items-center mt-8">
      <h1 class="figbold justify-start flex-grow">Dynamic</h1>
      <h1 class="figbold justify-end">Dynamic</h1>
    </div> -->

    <section class="flex items-center mt-16 pl-6 pr-2">
      <div class="floor isometric">
        <div class="sheet"></div>
      </div>

      <div class="h[28px] bg-black p-2 px-4 -translate-y-[2.1rem] ml-auto">
        <span class="text-xl figbold text-[#E8FBF8]">QR</span>
        <span class="text-white figbold text-lg">Codes</span>
      </div>
    </section>
    <div class="flex mt-8">
      <p class="pr-4 mt-1">👋</p>
      <p class="figlight text-lg">
        Create dynamic, branded, QR Codes with splash pages to get your sound
        out
      </p>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
/* stylelint-disable */

.isometric {
  -webkit-transform: rotateX(60deg) rotateY(0deg) rotateZ(45deg)
    translate(-38%, 38%) scale3d(1, 1, 1);
  -moz-transform: rotateX(60deg) rotateY(0deg) rotateZ(45deg)
    translate(-38%, 38%) scale3d(1, 1, 1);
  -ms-transform: rotateX(60deg) rotateY(0deg) rotateZ(45deg)
    translate(-38%, 38%) scale3d(1, 1, 1);
  -o-transform: rotateX(60deg) rotateY(0deg) rotateZ(45deg)
    translate(-38%, -38%) scale3d(1, 1, 1);
  transform: rotateX(60deg) rotateY(0deg) rotateZ(45deg) translate(-38%, -38%)
    scale3d(1, 1, 1);
}

.sheet {
  width: 80px;
  height: 80px;
  border-radius: 2px;
  background-image: url('https://cdn5.vectorstock.com/i/1000x1000/18/69/blue-qr-code-scanning-icon-or-design-logo-vector-18861869.jpg');
  background-position: center center;
  background-size: cover;
  /* background: #00cafe; */
  border-bottom: 2px solid;
  border-right: 2px solid;
  -webkit-animation: lift 1.5s ease-in-out alternate infinite;
  -moz-animation: lift 1.5s ease-in-out alternate infinite;
  animation: lift 1.5s ease-in-out alternate infinite;
  overflow: hidden;
  margin: -30px;
}

.floor {
  width: 80px;
  height: 80px;
  border-radius: 2px;
  background: #fefefe;
  border-bottom: 2px solid #cbcbcb;
  border-right: 2px solid #cbcbcb;
  padding: 10px;
}

@-webkit-keyframes lift {
  20%,
  from {
    -webkit-transform: translate(0, 0);
    box-shadow: -1px 2px 2px -2px rgba(0, 0, 0, 0.3);
  }
  80%,
  to {
    -webkit-transform: translate(-80px, -80px);
    box-shadow: 80px 112px 40px rgba(0, 0, 0, 0.2),
      80px 80px 40px rgba(0, 0, 0, 0.2);
  }
}
@-moz-keyframes lift {
  20%,
  from {
    -moz-transform: translate(0, 0);
    box-shadow: -1px 2px 2px -2px rgba(0, 0, 0, 0.3);
  }
  80%,
  to {
    -moz-transform: translate(-80px, -80px);
    box-shadow: 80px 112px 40px rgba(0, 0, 0, 0.2),
      80px 80px 40px rgba(0, 0, 0, 0.2);
  }
}
@keyframes lift {
  20%,
  from {
    -webkit-transform: translate(0, 0);
    -moz-transform: translate(0, 0);
    -ms-transform: translate(0, 0);
    -o-transform: translate(0, 0);
    transform: translate(0, 0);
    box-shadow: -1px 2px 2px -2px rgba(0, 0, 0, 0.3);
  }
  80%,
  to {
    -webkit-transform: translate(-80px, -80px);
    -moz-transform: translate(-80px, -80px);
    -ms-transform: translate(-80px, -80px);
    -o-transform: translate(-80px, -80px);
    transform: translate(-80px, -80px);
    box-shadow: 80px 112px 40px rgba(0, 0, 0, 0.2),
      80px 80px 40px rgba(0, 0, 0, 0.2);
  }
}
/* stylelint-enable */
</style>
