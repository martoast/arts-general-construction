<template>
  <div class="bg-white">
    <div
      class="mx-auto max-w-2xl px-4 py-24 sm:px-6 sm:py-32 lg:max-w-7xl lg:px-8"
    >
      <div
        class="grid grid-cols-1 items-center gap-x-8 gap-y-16 lg:grid-cols-2"
      >
        <div>
          <div class="border-b border-gray-200 pb-10">
            <h2 class="font-medium text-red-600">
              Full-Service General Contractor
            </h2>
            <p
              class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl"
            >
              Your Vision, Our Expertise
            </p>
            <p class="mt-4 text-lg text-gray-600">
              From permits to final touches, we handle every aspect of your
              construction project. With over 15 years of excellence, we're your
              single point of contact for turning your project into reality.
            </p>
          </div>
          <dl class="mt-10 space-y-10">
            <div v-for="service in services" :key="service.name">
              <dt class="flex items-center text-lg font-semibold text-gray-900">
                <component
                  :is="service.icon"
                  class="h-6 w-6 text-red-600 mr-2"
                />
                {{ service.name }}
              </dt>
              <dd class="mt-3 text-base text-gray-500">
                {{ service.description }}
              </dd>
            </div>
          </dl>
        </div>
        <div>
          <!-- Option 1: Using max-height directly -->
          <div
            class="overflow-hidden rounded-lg bg-gray-100"
            style="max-height: 500px"
          >
            <img
              src="/contrusction2.jpg"
              alt="Custom home construction project showcasing modern architecture and quality craftsmanship"
              class="h-full w-full object-cover object-center"
            />
          </div>

          <!-- Option 2: Using aspect ratio with max-height -->
          <!-- <div class="aspect-h-3 aspect-w-4 overflow-hidden rounded-lg bg-gray-100 max-h-[500px]">
              <img src="/contruction.jpg" alt="Custom home construction project showcasing modern architecture and quality craftsmanship" class="h-full w-full object-cover object-center" />
            </div> -->

          <div
            class="mt-4 grid grid-cols-2 gap-4 sm:mt-6 sm:gap-6 lg:mt-8 lg:gap-8"
          >
            <div
              class="aspect-h-1 aspect-w-1 overflow-hidden rounded-lg bg-gray-100"
            >
              <img
                src="/fillign.jpg"
                alt="Interior renovation showcasing kitchen remodeling with modern finishes"
                class="h-full w-full object-cover object-center"
              />
            </div>
            <div
              class="aspect-h-1 aspect-w-1 overflow-hidden rounded-lg bg-gray-100"
            >
              <img
                src="/concrete.jpg"
                alt="ADU construction project highlighting additional living space solutions"
                class="h-full w-full object-cover object-center"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
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
