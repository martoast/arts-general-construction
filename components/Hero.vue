<script setup>
const images = ref([
  '/house3.jpg',
  '/good.jpg',
  '/great.jpg',
  
])

const currentImageIndex = ref(0)

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.value.length
}

onMounted(() => {
  const interval = setInterval(nextImage, 5000)

  onUnmounted(() => clearInterval(interval))
})
</script>

<template>
  <div class="relative isolate h-screen" role="banner">
    <!-- Background image with enhanced overlay -->
    <div class="absolute inset-0" aria-hidden="true">
      <TransitionGroup name="fade">
        <img
          v-for="(image, index) in images"
          :key="image"
          :src="image"
          v-show="currentImageIndex === index"
          alt="View of our construction projects"
          class="absolute h-full w-full object-cover transition-opacity duration-1000"
        />
      </TransitionGroup>
      <div 
        class="absolute inset-0 bg-gradient-to-b from-gray-900/70 via-gray-900/50 to-gray-900/70" 
        aria-hidden="true" 
      />
    </div>

    <!-- Navigation bar -->
    <header class="absolute inset-x-0 top-0 z-10">
      <nav 
        class="mx-auto flex max-w-7xl items-center justify-between p-6 lg:px-8" 
        aria-label="Main navigation"
      >
        <div class="flex lg:flex-1">
          <a 
            href="/" 
            class="-m-1.5 p-1.5 transition-transform duration-300 hover:scale-105"
            aria-label="Art's General Construction - Home"
          >
            <img 
              class="h-14 w-auto drop-shadow-2xl" 
              src="/Artslogo.png" 
              alt="Art's General Construction logo" 
            />
          </a>
        </div>
      </nav>
    </header>

    <!-- Main hero content -->
    <div class="relative isolate px-6 pt-14 lg:px-8">
      <main class="mx-auto max-w-3xl py-32 sm:py-48">
        <div class="text-center">
          <h1 class="text-4xl font-bold tracking-tight text-white sm:text-6xl lg:text-7xl drop-shadow-2xl">
            Building San Diego's Homes and ADUs
          </h1>
          <p class="mt-8 text-lg leading-8 text-gray-100 max-w-xl mx-auto drop-shadow-lg font-medium">
            From custom homes to complete renovations, we bring exceptional craftsmanship and dedicated service to every project.
          </p>
          <div class="mt-12 flex flex-col items-center justify-center space-y-4 sm:space-y-0 sm:flex-row sm:space-x-6">
            <a
            
              href="#contact"
              class="group relative w-full sm:w-auto inline-flex items-center justify-center rounded-md bg-red-600 px-8 py-3.5 text-lg font-semibold text-white shadow-lg hover:bg-red-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-red-400 transition-all duration-300 ease-out hover:shadow-xl hover:-translate-y-0.5 min-h-[44px] min-w-[44px]"
              aria-label="Request a free consultation"
            >
              Get a free consultation
              <svg 
                class="ml-2.5 h-5 w-5 transition-transform duration-300 ease-out transform group-hover:translate-x-1" 
                fill="none" 
                viewBox="0 0 24 24" 
                stroke="currentColor"
                aria-hidden="true"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
              </svg>
            </a>
            <a 
              href="#services" 
              class="group relative w-full sm:w-auto inline-flex items-center justify-center rounded-md px-8 py-3.5 text-lg font-semibold text-white transition-all duration-300 ease-out hover:text-white/90 backdrop-blur-sm bg-white/10 hover:bg-white/20 border border-white/10 hover:border-white/20 min-h-[44px] min-w-[44px]"
              aria-label="View our services"
            >
              Our Services
              <svg 
                class="ml-2.5 h-5 w-5 transition-transform duration-300 ease-out transform group-hover:translate-x-1" 
                fill="none" 
                viewBox="0 0 24 24" 
                stroke="currentColor"
                aria-hidden="true"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
              </svg>
            </a>
          </div>
        </div>
      </main>
    </div>

    <!-- Scroll indicator -->
    <div 
      class="hidden md:block absolute bottom-10 left-1/2 transform -translate-x-1/2"
      aria-hidden="true"
    >
      <div class="flex flex-col items-center space-y-2">
        <span class="text-sm font-medium text-white/80 tracking-wider">Scroll to explore</span>
        <div class="w-8 h-14 border-2 border-white/20 rounded-full flex items-start justify-center p-2">
          <div class="w-1 h-3 bg-white rounded-full animate-scroll"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@keyframes scroll {
  0% {
    transform: translateY(0);
    opacity: 1;
  }
  100% {
    transform: translateY(28px);
    opacity: 0;
  }
}

.animate-scroll {
  animation: scroll 2s cubic-bezier(0.65, 0, 0.35, 1) infinite;
}
</style>