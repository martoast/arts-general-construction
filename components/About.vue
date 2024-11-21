<template>
  <section class="overflow-hidden bg-white py-24 sm:py-32" aria-labelledby="about-heading">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <!-- Header -->
      <div class="text-center mb-20">
        <h2 id="about-heading" class="text-base font-semibold text-red-600">About us</h2>
        <p class="mt-2 text-4xl font-bold tracking-tight text-gray-900 sm:text-5xl">In Business Since 2008</p>
      </div>

      <!-- Services List -->
      <div v-for="service in services" :key="service.title" class="mt-20 first:mt-0">
        <div class="mx-auto grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 sm:gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-2 lg:items-start">
          <!-- Service Details -->
          <div class="lg:pr-4 lg:pt-4">
            <div class="lg:max-w-xl">
              <h3 class="text-base/7 font-semibold text-red-600">{{ service.tagline }}</h3>
              <p class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">{{ service.title }}</p>
              <p class="mt-6 text-lg/8 text-gray-600">{{ service.description }}</p>
              
              <!-- Testimonial -->
              <figure class="mt-4 border-l border-gray-200 pl-8 text-gray-600">
                <blockquote>
                  <p>"{{ service.testimonial.quote }}"</p>
                </blockquote>
                <figcaption class="mt-6 flex gap-x-4 text-sm/6">
                  <img :src="service.testimonial.avatar || 'placeholder.png'" :alt="service.testimonial.author" class="h-6 w-6 flex-none rounded-full" />
                  <div><span class="font-semibold text-gray-900">{{ service.testimonial.author }}</span> – {{ service.testimonial.location }}</div>
                </figcaption>
              </figure>
            </div>
          </div>
          
          <!-- Carousel -->
          <div class="relative overflow-hidden rounded-xl" :aria-label="`${service.title} image carousel`" role="region">
            <!-- Images -->
            <div 
              class="flex transition-transform duration-500 ease-in-out"
              :style="{ transform: `translateX(-${currentImageIndexes[service.title] * 100}%)` }"
              role="presentation"
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
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-1 sm:space-x-2 z-10" role="tablist">
              <button
                v-for="(_, index) in service.images"
                :key="index"
                @click="setImageIndex(service.title, index)"
                class="w-12 h-12 sm:w-8 sm:h-8 rounded-full transition-colors duration-200 flex items-center justify-center"
                :class="currentImageIndexes[service.title] === index ? 'bg-red-600' : 'bg-gray-300'"
                :aria-label="`Show image ${index + 1} of ${service.images.length}`"
                :aria-selected="currentImageIndexes[service.title] === index"
                role="tab"
              >
                <span class="sr-only">Image {{ index + 1 }}</span>
                <div class="w-2 h-2 rounded-full" :class="currentImageIndexes[service.title] === index ? 'bg-white' : 'bg-gray-400'"></div>
              </button>
            </div>

            <!-- Navigation Arrows -->
            <button 
              @click="previousImage(service.title)" 
              class="absolute left-2 sm:left-4 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full w-12 h-12 sm:w-10 sm:h-10 flex items-center justify-center shadow-lg hover:bg-white transition-colors duration-200"
              aria-label="Previous image"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                class="w-6 h-6"
                aria-hidden="true"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
              </svg>
            </button>
            <button 
              @click="nextImage(service.title)" 
              class="absolute right-2 sm:right-4 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full w-12 h-12 sm:w-10 sm:h-10 flex items-center justify-center shadow-lg hover:bg-white transition-colors duration-200"
              aria-label="Next image"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                class="w-6 h-6"
                aria-hidden="true"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
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
      "/wow.jpg",
      "/house.jpg",
      "/house2.jpg",
      "/house3.jpg",
      "kitchen.jpeg"
    ],
    imageAlt: "Custom home construction project",
    testimonial: {
      quote: "Art's team made our dream home a reality. Their attention to detail and communication throughout the build was exceptional. We couldn't be happier with the result.",
      author: "Michael Rodriguez",
      location: "La Jolla, San Diego",
      avatar: "https://images.unsplash.com/photo-1509783236416-c9ad59bae472?ixlib=rb-=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80"
    }
  }
]

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