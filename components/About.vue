<template>
  <div class="overflow-hidden bg-white py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <!-- Services Header -->
      <div class="text-center mb-20">
        <h2 class="text-base font-semibold text-red-600">About us</h2>
        <p class="mt-2 text-4xl font-bold tracking-tight text-gray-900 sm:text-5xl">
          In Business Since 2008
        </p>
      </div>

      <!-- Services List -->
      <div v-for="service in services" :key="service.title" class="mt-20 first:mt-0">
        <div class="mx-auto grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 sm:gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-2 lg:items-start">
          <div class="lg:pr-4 lg:pt-4">
            <div class="lg:max-w-xl">
              <h2 class="text-base/7 font-semibold text-red-600">{{ service.tagline }}</h2>
              <p class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">{{ service.title }}</p>
              <p class="mt-6 text-lg/8 text-gray-600">{{ service.description }}</p>
              
              <figure class="mt-4 border-l border-gray-200 pl-8 text-gray-600">
                <blockquote class="text-base/7">
                  <p>"{{ service.testimonial.quote }}"</p>
                </blockquote>
                <figcaption class="mt-6 flex gap-x-4 text-sm/6">
                  <img src="https://images.unsplash.com/photo-1509783236416-c9ad59bae472?ixlib=rb-=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80" alt="" class="h-6 w-6 flex-none rounded-full" />
                  <div><span class="font-semibold text-gray-900">{{ service.testimonial.author }}</span> – {{ service.testimonial.location }}</div>
                </figcaption>
              </figure>
            </div>
          </div>
          
          <!-- Slideshow Section -->
          <div class="relative overflow-hidden rounded-xl">
            <!-- Image Container with Transform -->
            <div 
              class="flex transition-transform duration-500 ease-in-out"
              :style="{
                transform: `translateX(-${currentImageIndexes[service.title] * 100}%)`
              }"
            >
              <img 
                v-for="(image, idx) in service.images"
                :key="idx"
                :src="image" 
                :alt="`${service.imageAlt} ${idx + 1}`"
                class="flex-shrink-0 w-full object-cover rounded-xl shadow-xl ring-1 ring-gray-400/10"
              />
            </div>

            <!-- Navigation Dots -->
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-2 z-10">
              <button
                v-for="(_, index) in service.images"
                :key="index"
                @click="setImageIndex(service.title, index)"
                class="w-2 h-2 rounded-full transition-colors duration-200"
                :class="currentImageIndexes[service.title] === index ? 'bg-red-600' : 'bg-gray-300'"
              />
            </div>

            <!-- Navigation Arrows -->
            <button 
              @click="previousImage(service.title)" 
              class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full p-2 shadow-lg hover:bg-white transition-colors duration-200"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
              </svg>
            </button>
            <button 
              @click="nextImage(service.title)" 
              class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full p-2 shadow-lg hover:bg-white transition-colors duration-200"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg>
            </button>
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
    tagline: "Custom Home Construction",
    title: "Building Your Dream Home",
    description: "Art's General Construction has been transforming San Diego homes and spaces for over 15 years. As a full-service construction and remodeling company, we handle every aspect of your project from initial concept to final inspection. Our commitment to quality craftsmanship and attention to detail has made us one of San Diego's most trusted names in construction.",
    images: [
      "/house.jpg",
      "/house2.jpg",
      "/house3.jpg",
      "kitchen.jpeg"
    ],
    imageAlt: "Custom home construction project",
    testimonial: {
      quote: "Art's team made our dream home a reality. Their attention to detail and communication throughout the build was exceptional. We couldn't be happier with the result.",
      author: "Michael Rodriguez",
      location: "La Jolla, San Diego"
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