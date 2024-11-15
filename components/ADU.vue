<template>
  <div class="overflow-hidden bg-white">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div v-for="service in services" :key="service.title" class="mt-20 first:mt-0">
        <div class="mx-auto grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 sm:gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-2 lg:items-start">
          <!-- Slideshow Section - Optimized for vertical images -->
          <div class="relative h-[600px] lg:h-[700px] overflow-hidden rounded-xl order-last lg:order-first">
            <div 
              class="flex h-full transition-transform duration-500 ease-in-out"
              :style="{
                transform: `translateX(-${currentImageIndexes[service.title] * 100}%)`
              }"
            >
              <img 
                v-for="(image, idx) in service.images"
                :key="idx"
                :src="image" 
                :alt="`${service.imageAlt} ${idx + 1}`"
                class="flex-shrink-0 w-full h-full object-cover object-center rounded-xl shadow-xl ring-1 ring-gray-400/10"
              />
            </div>

            <!-- Navigation Dots -->
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-3 z-10">
              <button
                v-for="(_, index) in service.images"
                :key="index"
                @click="setImageIndex(service.title, index)"
                class="w-3 h-3 rounded-full transition-colors duration-200 shadow-md"
                :class="currentImageIndexes[service.title] === index ? 'bg-red-600' : 'bg-white/80'"
              />
            </div>

            <!-- Navigation Arrows -->
            <button 
              @click="previousImage(service.title)" 
              class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white/90 rounded-full p-3 shadow-lg hover:bg-white transition-colors duration-200"
              aria-label="Previous image"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                class="w-6 h-6 text-gray-700"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
              </svg>
            </button>
            <button 
              @click="nextImage(service.title)" 
              class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white/90 rounded-full p-3 shadow-lg hover:bg-white transition-colors duration-200"
              aria-label="Next image"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                class="w-6 h-6 text-gray-700"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg>
            </button>

            <!-- Image Counter -->
            <div class="absolute top-4 right-4 bg-black/50 text-white px-3 py-1 rounded-full text-sm">
              {{ currentImageIndexes[service.title] + 1 }} / {{ service.images.length }}
            </div>
          </div>

          <!-- Content Section -->
          <div class="lg:pl-4 lg:pt-4 order-first lg:order-last">
            <div class="lg:max-w-xl">
              <h2 class="text-base/7 font-semibold text-red-600">{{ service.tagline }}</h2>
              <p class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">{{ service.title }}</p>
              <p class="mt-6 text-lg/8 text-gray-600">{{ service.description }}</p>
              
              <figure class="mt-8 border-l border-gray-200 pl-8 text-gray-600">
                <blockquote class="text-base/7">
                  <p>"{{ service.testimonial.quote }}"</p>
                </blockquote>
                <figcaption class="mt-6 flex gap-x-4 text-sm/6">
                  <img src="/JL.jpeg" alt="" class="h-6 w-6 flex-none rounded-full bg-gray-50" />
                  <div>
                    <span class="font-semibold text-gray-900">{{ service.testimonial.author }}</span>
                    <br />
                    {{ service.testimonial.location }}
                  </div>
                </figcaption>
              </figure>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue'
  
  const currentImageIndexes = ref({})
  let autoScrollInterval = null
  
  const services = [
    {
      tagline: "Full-Service ADU Solutions",
      title: "Your ADU Journey Made Simple",
      description: "From permits to completion, we handle every aspect of your ADU project. Our comprehensive service includes design consultation, permit acquisition, construction, and final inspections. We specialize in maximizing your property's potential while navigating San Diego's ADU regulations. Our experienced team ensures a smooth process, delivering high-quality additional living spaces that add value to your property.",
      images: [
        '/jl/20240729_154524.jpg',
        
        '/jl/20240807_092928.jpg',
        
        "/aduproces1.jpg",
        '/jl/20240818_195427.jpg',
        "/foundation.jpg",
        '/jl/20240827_114413.jpg',
        
        '/jl/20241113_104612.jpg',
        '/jl/20241001_180044.jpg'
        
      ],
      imageAlt: "Custom ADU construction project",
      testimonial: {
        quote: "Art's team guided us through the entire ADU process. They handled all the permits, designed a beautiful space, and completed construction ahead of schedule. The rental income from our ADU has been a game-changer.",
        author: "Jose Samperio",
        location: "Eastlake, San Diego"
      }
    }
  ]
  
  // Initialize currentImageIndexes for each service
  onMounted(() => {
    services.forEach(service => {
      currentImageIndexes.value[service.title] = 0
    })
    startAutoScroll()
  })
  
  onUnmounted(() => {
    if (autoScrollInterval) {
      clearInterval(autoScrollInterval)
    }
  })
  
  const setImageIndex = (serviceTitle, index) => {
    currentImageIndexes.value[serviceTitle] = index
  }
  
  const nextImage = (serviceTitle) => {
    const service = services.find(s => s.title === serviceTitle)
    if (service) {
      currentImageIndexes.value[serviceTitle] = 
        (currentImageIndexes.value[serviceTitle] + 1) % service.images.length
    }
  }
  
  const previousImage = (serviceTitle) => {
    const service = services.find(s => s.title === serviceTitle)
    if (service) {
      currentImageIndexes.value[serviceTitle] = 
        (currentImageIndexes.value[serviceTitle] - 1 + service.images.length) % service.images.length
    }
  }
  
  const startAutoScroll = () => {
    autoScrollInterval = setInterval(() => {
      services.forEach(service => {
        nextImage(service.title)
      })
    }, 5000)
  }
  </script>
  
  <style scoped>
  .flex > img {
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }
  </style>