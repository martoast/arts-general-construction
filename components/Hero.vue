<template>
  <div class="relative isolate h-screen">
    <!-- Background image with overlay -->
    <div class="absolute inset-0">
      <img
        src="/contruction.jpg"
        alt="Modern construction project"
        class="h-full w-full object-cover"
      />
      <div class="absolute inset-0 bg-gray-900/40 mix-blend-multiply" aria-hidden="true" />
    </div>

    <!-- Navigation bar placeholder - you can customize or remove this -->
    <div class="absolute inset-x-0 top-0 z-10">
      <nav class="mx-auto flex max-w-7xl items-center justify-between p-6 lg:px-8" aria-label="Global">
        <div class="flex lg:flex-1">
          <a href="#" class="-m-1.5 p-1.5">
            <span class="sr-only">Art's General Construction</span>
            <!-- Add your logo here -->
            <img class="h-14 w-auto" src="/Artslogo.png" alt="Company logo" />
          </a>
        </div>
      </nav>
    </div>

    <!-- Hero content -->
    <div class="relative isolate px-6 pt-14 lg:px-8">
      <div class="mx-auto max-w-3xl py-32 sm:py-48">
        <div class="text-center">
          <h1 class="text-4xl font-bold tracking-tight text-white sm:text-6xl lg:text-7xl">
            Transforming San Diego Homes and ADU's
          </h1>
          <p class="mt-6 text-lg leading-8 text-gray-100 max-w-xl mx-auto">
            From custom homes to complete renovations, we bring exceptional craftsmanship and dedicated service to every project.
          </p>
          <div class="mt-10 flex flex-col items-center justify-center space-y-4 sm:space-y-0 sm:flex-row sm:space-x-6">
            <a
              href="#contact"
              class="w-full sm:w-auto rounded-md bg-red-600 px-6 py-3 text-lg font-semibold text-white shadow-sm hover:bg-orange-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-orange-400 transition-colors duration-200 text-center"
            >
              Get a free consultation
            </a>
            <a 
              href="#services" 
              class="w-full sm:w-auto text-lg font-semibold leading-6 text-white hover:text-orange-200 transition-colors duration-200 py-3 text-center border border-white/20 rounded-md hover:bg-white/10 sm:border-0 sm:bg-transparent"
            >
              Our Services <span aria-hidden="true">→</span>
            </a>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
      <svg
        class="h-6 w-6 text-white"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
      </svg>
    </div>
  </div>
</template>