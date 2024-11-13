<template>
  <div class="bg-white">
    <div class="mx-auto max-w-2xl px-4 py-24 sm:px-6 sm:py-32 lg:max-w-7xl lg:px-8">
      <div class="grid grid-cols-1 items-center gap-x-8 gap-y-16 lg:grid-cols-2">
        <!-- Services Info Section -->
        <div>
          <div class="border-b border-gray-200 pb-10">
            <h2 class="font-medium text-red-600">Full-Service General Contractor</h2>
            <p class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">
              Your Vision, Our Expertise
            </p>
            <p class="mt-4 text-lg text-gray-600">
              From permits to final touches, we handle every aspect of your construction project. With over 15 years of excellence, we're your single point of contact for turning your project into reality.
            </p>
          </div>
          <dl class="mt-10 space-y-10">
            <div v-for="service in services" :key="service.name">
              <dt class="flex items-center text-lg font-semibold text-gray-900">
                <component :is="service.icon" class="h-6 w-6 text-red-600 mr-2" />
                {{ service.name }}
              </dt>
              <dd class="mt-3 text-base text-gray-500">{{ service.description }}</dd>
            </div>
          </dl>
        </div>

        <!-- Gallery Section -->
        <div>
          <!-- Main image -->
          <div
            class="overflow-hidden rounded-lg bg-gray-100 cursor-zoom-in group relative"
            style="max-height: 500px"
            @click="openModal(0)"
          >
            <div class="absolute inset-0 bg-black bg-opacity-0 group-hover:bg-opacity-30 transition-all duration-300 flex items-center justify-center">
              <div class="text-white opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col items-center">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="w-8 h-8 mb-2">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7" />
                </svg>
                <span class="text-sm font-medium">Click to expand</span>
              </div>
            </div>
            <img
              :src="galleryImages[0]"
              alt="Custom home construction project showcasing modern architecture and quality craftsmanship"
              class="h-full w-full object-cover object-center"
            />
          </div>

          <!-- Smaller images grid -->
          <div class="mt-4 grid grid-cols-2 gap-4 sm:mt-6 sm:gap-6 lg:mt-8 lg:gap-8">
            <div
              v-for="(image, index) in galleryImages.slice(1)"
              :key="index + 1"
              class="aspect-h-1 aspect-w-1 overflow-hidden rounded-lg bg-gray-100 cursor-zoom-in group relative"
              @click="openModal(index + 1)"
            >
              <div class="absolute inset-0 bg-black bg-opacity-0 group-hover:bg-opacity-30 transition-all duration-300 flex items-center justify-center">
                <div class="text-white opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="w-6 h-6 mb-1">
                    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7" />
                  </svg>
                  <span class="text-xs font-medium">Click to expand</span>
                </div>
              </div>
              <img
                :src="image"
                :alt="imageAlts[index + 1]"
                class="h-full w-full object-cover object-center"
              />
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Enhanced Modal Carousel -->
    <ModalCarousel
      :showModal="isModalOpen"
      :images="galleryImages"
      :startIndex="selectedImageIndex"
      @close="isModalOpen = false"
    />
  </div>
</template>

<script setup>
import {
  HomeIcon,
  BuildingOffice2Icon,
  WrenchScrewdriverIcon,
  PlusIcon,
  ClipboardDocumentCheckIcon,
} from "@heroicons/vue/24/outline";
import { ref } from 'vue';

const isModalOpen = ref(false);
const selectedImageIndex = ref(0);

// Gallery images with their paths
const galleryImages = [
  '/contrusction2.jpg',
  '/foundation3.jpg',
  '/nice.jpg',
  '/great.jpg',
  '/fullhouse.jpg'
];

// Alt texts for accessibility
const imageAlts = [
  'Custom home construction project showcasing modern architecture and quality craftsmanship',
  'Interior renovation showcasing kitchen remodeling with modern finishes',
  'ADU construction project highlighting additional living space solutions'
];

function openModal(index) {
  selectedImageIndex.value = index;
  isModalOpen.value = true;
}

// Services data
const services = [
  {
    name: "Custom Home Building",
    description:
      "We specialize in creating bespoke homes that perfectly match your vision and lifestyle. Our experienced team ensures exceptional quality and craftsmanship throughout every phase of construction.",
    icon: HomeIcon,
  },
  {
    name: "Home Renovation",
    description:
      "Transform your existing space with our comprehensive renovation services. From kitchen and bathroom remodels to whole-house renovations, we bring modern functionality while preserving your home's character.",
    icon: WrenchScrewdriverIcon,
  },
  {
    name: "Additions and Extensions",
    description:
      "Expand your living space with seamlessly integrated additions and extensions. We handle everything from design and permits to construction, ensuring your new space blends perfectly with your existing home.",
    icon: PlusIcon,
  },
  {
    name: "Outdoor Living Spaces",
    description:
      "Create your perfect outdoor retreat with custom patios, decks, and outdoor kitchens. We design and build beautiful, functional outdoor spaces that extend your living area and enhance your lifestyle.",
    icon: BuildingOffice2Icon,
  },
  {
    name: "Project Management",
    description:
      "Our dedicated project management ensures your construction project runs smoothly from start to finish. We coordinate all aspects of the build, maintaining clear communication and adherence to timelines and budgets.",
    icon: ClipboardDocumentCheckIcon,
  },
];
</script>