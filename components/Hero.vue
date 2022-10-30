<template>
  <div>
    <section class="flex items-center mt-16 pl-6 pr-2 sm:hidden">
      <div class="floor isometric">
        <div class="sheet"></div>
      </div>

      <div class="h[28px] bg-black p-2 px-4 -translate-y-[2.1rem] ml-auto">
        <span class="text-xl figbold text-[#E8FBF8]">QR</span>
        <span class="text-white figbold text-lg">Codes</span>
      </div>
    </section>

    <div class="bg-white">
      <div class="mx-auto max-w-7xl py-16 px-2 sm:px-6 lg:py-24 lg:px-8">
        <div class="mx-auto max-w-3xl text-center">
          <h2 class="text-3xl font-bold tracking-tight text-gray-900 figbold">
            Create Dynamic Branded QR Codes
          </h2>
          <p class="mt-4 text-lg text-gray-500">
            Full customizable landing pages are included with your QR Codes
          </p>
        </div>
        <dl
          class="mt-12 space-y-10 sm:grid sm:grid-cols-2 sm:gap-x-6 sm:gap-y-12 sm:space-y-0 lg:grid-cols-4 lg:gap-x-8"
        >
          <div v-for="feature in features" :key="feature.name" class="relative">
            <dt>
              <p class="ml-4 text-lg leading-6 text-gray-900 font-bold figbold">
                {{ feature.name }}
              </p>
            </dt>
            <dd class="mt-2 ml-4 text-base text-gray-500">
              {{ feature.description }}
            </dd>
          </div>
        </dl>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      features: [
        {
          name: 'Change the function of your QR code ',
          description:
            'Link to a website today and then to an event landing pages tomorrow. Make as many changes as you want',
        },
        {
          name: 'Tracking Analytics',
          description: 'Keep track of how many scans you get per QR code',
        },
        {
          name: 'Adding new landing pages and features all the time ',
          description:
            'We are constantly listening to what are users want, so we can build the features you are asking for',
        },
        {
          name: 'Full hosted landing pages, no coding required',
          description:
            'We host the landing pages for you with no setup required ',
        },
      ],
    }
  },
}
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
li {
  list-style: square;
  margin-top: 0.8em;
}
/* stylelint-enable */
</style>
