<template>
  <div class="relative">
    <main class="lg:relative">
      <div
        class="mx-auto w-full max-w-7xl pt-16 pb-20 text-center lg:py-48 lg:text-left"
      >
        <div class="px-4 sm:px-8 lg:w-1/2 xl:pr-16">
          <h1
            class="text-4xl font-bold figbold tracking-tight text-gray-900 sm:text-5xl md:text-6xl lg:text-5xl xl:text-6xl"
          >
            <span class="block xl:inline">Dynamic Qr Codes</span>
            {{ ' ' }}
            <span class="block text-[#00FFD7] mt-4 xl:inline"
              >Music Industry</span
            >
          </h1>
          <p
            class="mx-auto mt-3 max-w-md text-lg text-gray-500 sm:text-xl md:mt-5 md:max-w-3xl"
          >
            Create branded QR codes with landing pages and dynamic functionality
            to get your sound out
          </p>
          <div class="mt-14 sm:flex sm:justify-center lg:justify-start">
            <div class="rounded-md shadow">
              <nuxt-link
                to="/signup"
                class="flex w-full items-center justify-center rounded-md border border-transparent bg-black px-8 py-3 text-base fig text-[#00FFD7] hover:bg-indigo-700 md:py-4 md:px-10 md:text-lg"
                >Get started</nuxt-link
              >
            </div>
            <div class="mt-6 rounded-md shadow sm:mt-0 sm:ml-3">
              <nuxt-link
                to="/login"
                class="flex w-full items-center justify-center rounded-md border border-transparent bg-white px-8 py-3 text-base fig text-black hover:bg-gray-50 md:py-4 md:px-10 md:text-lg"
                >Login</nuxt-link
              >
            </div>
          </div>
        </div>
      </div>
      <div
        class="relative flex items-center h-64 w-full sm:h-72 md:h-96 lg:absolute lg:inset-y-0 lg:right-0 lg:h-full lg:w-1/2"
      >
        <!-- Put Qr Code here -->
        <NuxtImg src="/codeone.png" alt="" class="mx-auto" />
      </div>
    </main>
  </div>
</template>
