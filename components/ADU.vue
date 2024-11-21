<template>
  <section class="overflow-hidden bg-white" aria-labelledby="adu-section">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div
        v-for="service in services"
        :key="service.title"
        class="mt-20 first:mt-0"
      >
        <div
          class="mx-auto grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 sm:gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-2 lg:items-start"
        >
          <!-- Carousel Section -->
          <div
            class="relative overflow-hidden rounded-xl order-last lg:order-first h-96"
            role="region"
            aria-label="Project images carousel"
          >
            <div
              class="flex h-full transition-transform duration-500 ease-in-out"
              :style="{
                transform: `translateX(-${
                  currentImageIndexes[service.title] * 100
                }%)`,
              }"
              role="presentation"
            >
              <img
                v-for="(image, idx) in service.images"
                :key="idx"
                :src="image"
                :alt="`${service.imageAlt} - Progress photo ${idx + 1} of ${
                  service.images.length
                }`"
                class="flex-shrink-0 w-full object-cover rounded-xl shadow-xl ring-1 ring-gray-400/10"
              />
            </div>

            <!-- Navigation Controls -->
            <div
              class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-1 sm:space-x-2 z-10"
              role="tablist"
            >
              <button
                v-for="(_, index) in service.images"
                :key="index"
                @click="setImageIndex(service.title, index)"
                class="w-12 h-12 sm:w-8 sm:h-8 rounded-full transition-colors duration-200 flex items-center justify-center"
                :class="
                  currentImageIndexes[service.title] === index
                    ? 'bg-red-600'
                    : 'bg-gray-300'
                "
                :aria-label="`Show image ${index + 1} of ${
                  service.images.length
                }`"
                :aria-selected="currentImageIndexes[service.title] === index"
                role="tab"
              >
                <div
                  class="w-2 h-2 rounded-full"
                  :class="
                    currentImageIndexes[service.title] === index
                      ? 'bg-white'
                      : 'bg-gray-400'
                  "
                ></div>
              </button>
            </div>

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
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M15 19l-7-7 7-7"
                />
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
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </button>
          </div>

          <!-- Content Section -->
          <div class="lg:pl-4 lg:pt-4 order-first lg:order-last">
            <div class="lg:max-w-xl">
              <h2
                id="adu-section"
                class="text-base/7 font-semibold text-red-600"
              >
                {{ service.tagline }}
              </h2>
              <p
                class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl"
              >
                {{ service.title }}
              </p>
              <p class="mt-6 text-lg/8 text-gray-600">
                {{ service.description }}
              </p>

              <figure class="mt-4 border-l border-gray-200 pl-8 text-gray-600">
                <blockquote>
                  <p>"{{ service.testimonial.quote }}"</p>
                </blockquote>
                <figcaption class="mt-6 flex gap-x-4 text-sm/6">
                  <img
                    :src="service.testimonial.avatar || '/placeholder.png'"
                    :alt="`${service.testimonial.author}'s avatar`"
                    class="h-6 w-6 flex-none rounded-full"
                  />
                  <div>
                    <span class="font-semibold text-gray-900">{{
                      service.testimonial.author
                    }}</span>
                    – {{ service.testimonial.location }}
                  </div>
                </figcaption>
              </figure>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const currentImageIndexes = ref({});
let autoScrollInterval = null;

const services = [
  {
    tagline: "Full-Service ADU Solutions",
    title: "Your ADU Journey Made Simple",
    description:
      "From permits to completion, we handle every aspect of your ADU project. Our comprehensive service includes design consultation, permit acquisition, construction, and final inspections. We specialize in maximizing your property's potential while navigating San Diego's ADU regulations. Our experienced team ensures a smooth process, delivering high-quality additional living spaces that add value to your property.",
    images: [
      // "/jl/20240729_154524.jpg",

      "/jl/20240801_185002.jpg",
      "/jl/20240807_072821.jpg",
      "/jl/20240818_195427 (1).jpg",
      "/jl/20240827_094138 (1).jpg",
      "/jl/20240827_114413 (1).jpg",
      "/jl/20240827_155551 (1).jpg",
      "/jl/20240928_104521.jpg",
      "jl/20241113_104941 (1).jpg",
    ],
    imageAlt: "Custom ADU construction project",
    testimonial: {
      quote:
        "Art's team guided us through the entire ADU process. They handled all the permits, designed a beautiful space, and completed construction ahead of schedule. The rental income from our ADU has been a game-changer.",
      author: "Jose Samperio",
      location: "Eastlake, San Diego",
      avatar: "/JL.jpeg"
    },
  },
];

// Initialize currentImageIndexes for each service
onMounted(() => {
  services.forEach((service) => {
    currentImageIndexes.value[service.title] = 0;
  });
  startAutoScroll();
});

onUnmounted(() => {
  if (autoScrollInterval) {
    clearInterval(autoScrollInterval);
  }
});

const setImageIndex = (serviceTitle, index) => {
  currentImageIndexes.value[serviceTitle] = index;
};

const nextImage = (serviceTitle) => {
  const service = services.find((s) => s.title === serviceTitle);
  if (service) {
    currentImageIndexes.value[serviceTitle] =
      (currentImageIndexes.value[serviceTitle] + 1) % service.images.length;
  }
};

const previousImage = (serviceTitle) => {
  const service = services.find((s) => s.title === serviceTitle);
  if (service) {
    currentImageIndexes.value[serviceTitle] =
      (currentImageIndexes.value[serviceTitle] - 1 + service.images.length) %
      service.images.length;
  }
};

const startAutoScroll = () => {
  autoScrollInterval = setInterval(() => {
    services.forEach((service) => {
      nextImage(service.title);
    });
  }, 5000);
};
</script>

<style scoped>
.flex > img {
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
</style>
