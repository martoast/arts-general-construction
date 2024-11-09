<template>
  <div ref="componentRef" class="bg-white py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <!-- Header -->
      <div class="mx-auto max-w-2xl text-center">
        <h2 class="text-base font-semibold text-red-600">Testimonials</h2>
        <p class="mt-2 text-4xl font-bold tracking-tight text-gray-900 sm:text-5xl">
          What Our Clients Say
        </p>
        <p class="mt-4 text-lg text-gray-600">
          Hear from satisfied homeowners across San Diego about their experience with Art's General Construction.
        </p>
      </div>

      <!-- Carousel Section -->
      <div class="mt-16 relative" @mouseenter="pauseAutoScroll" @mouseleave="resumeAutoScroll">
        <!-- Left Arrow -->
        <button
          @click="scrollLeft"
          class="absolute left-0 top-1/2 transform -translate-y-1/2 bg-white/80 hover:bg-white shadow-lg rounded-full p-3 z-10 transition-colors duration-200"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            class="h-6 w-6 text-gray-900"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>

        <!-- Testimonials Container -->
        <div ref="scrollContainer" class="flex overflow-x-auto space-x-6 py-4 px-8 hide-scrollbar">
          <!-- Individual Testimonial Cards -->
          <div v-for="(testimonial, index) in testimonials" :key="index" class="flex-none w-[384px]">
            <div class="group relative h-[400px]">
              <!-- Gradient border wrapper -->
              <div class="absolute -inset-1 rounded-2xl bg-gradient-to-r from-orange-200 via-gray-400 to-orange-500 opacity-75 blur transition duration-500 group-hover:opacity-100"></div>

              <!-- Card Content -->
              <div class="relative h-full rounded-2xl bg-white p-8 transition-all duration-300 group-hover:transform group-hover:scale-[1.02] flex flex-col border border-gray-200">
                <!-- Star Rating -->
                <div class="flex gap-1 mb-6 flex-shrink-0">
                  <svg v-for="star in 5" :key="star" class="h-5 w-5 text-yellow-500" fill="currentColor" viewBox="0 0 20 20">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                  </svg>
                </div>

                <!-- Testimonial Text -->
                <p class="text-lg text-gray-600 flex-grow overflow-y-auto">{{ testimonial.body }}</p>

                <!-- Author Info -->
                <div class="flex items-center mt-8 flex-shrink-0">
                  <img :src="testimonial.author.imageUrl" :alt="testimonial.author.name" class="h-12 w-12 rounded-full object-cover" />
                  <div class="ml-4">
                    <h4 class="text-base font-semibold text-gray-900">{{ testimonial.author.name }}</h4>
                    <p class="text-sm text-gray-500">{{ testimonial.author.location }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Right Arrow -->
        <button
          @click="scrollRight"
          class="absolute right-0 top-1/2 transform -translate-y-1/2 bg-white/80 hover:bg-white shadow-lg rounded-full p-3 z-10 transition-colors duration-200"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            class="h-6 w-6 text-gray-900"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const testimonials = ref([
  {
    body: "Art's team transformed our outdated kitchen into a stunning modern space. Their attention to detail and craftsmanship was exceptional. The project was completed on time and within budget, making the entire renovation process stress-free.",
    author: {
      name: "Sarah Johnson",
      location: "Chula Vista, San Diego",
      imageUrl: "https://images.unsplash.com/photo-1509783236416-c9ad59bae472?ixlib=rb-=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80"
    }
  },
  {
    body: "The home addition project exceeded our expectations. Art's team handled everything from permits to final touches. Their expertise in navigating San Diego's building codes was invaluable, and the results are absolutely beautiful.",
    author: {
      name: "Michael Chen",
      location: "Pacific Beach, San Diego",
      imageUrl: "https://images.unsplash.com/photo-1509783236416-c9ad59bae472?ixlib=rb-=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80"
    }
  },
  {
    body: "We hired Art's General Construction for a complete home remodel, and they delivered beyond our dreams. Their communication throughout the project was excellent, and their craftsmanship is unmatched.",
    author: {
      name: "Emily Rodriguez",
      location: "Carmel Valley, San Diego",
      imageUrl: "https://images.unsplash.com/photo-1509783236416-c9ad59bae472?ixlib=rb-=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80"
    }
  },
  {
    body: "The custom home building process with Art was seamless. Their team's expertise and dedication to quality were evident at every step. They turned our vision into reality while keeping everything on schedule.",
    author: {
      name: "David Thompson",
      location: "Del Mar, San Diego",
      imageUrl: "https://images.unsplash.com/photo-1509783236416-c9ad59bae472?ixlib=rb-=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80"
    }
  },
  {
    body: "Art's team handled our bathroom renovation with incredible skill. Their design suggestions were spot-on, and the quality of work is outstanding. We're already planning our next project with them.",
    author: {
      name: "Chris Patel",
      location: "Coronado, San Diego",
      imageUrl: "https://images.unsplash.com/photo-1509783236416-c9ad59bae472?ixlib=rb-=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80"
    }
  }
]);

const componentRef = ref(null);
const scrollContainer = ref(null);
let autoScrollInterval = null;
let observer = null;

const scrollLeft = () => {
  scrollContainer.value.scrollBy({ left: -400, behavior: "smooth" });
};

const scrollRight = () => {
  scrollContainer.value.scrollBy({ left: 400, behavior: "smooth" });
};

const startAutoScroll = () => {
  autoScrollInterval = setInterval(() => {
    if (scrollContainer.value) {
      const isAtEnd =
        scrollContainer.value.scrollLeft + scrollContainer.value.clientWidth >=
        scrollContainer.value.scrollWidth;
      if (isAtEnd) {
        scrollContainer.value.scrollTo({ left: 0, behavior: "smooth" });
      } else {
        scrollRight();
      }
    }
  }, 3000);
};

const pauseAutoScroll = () => {
  if (autoScrollInterval) {
    clearInterval(autoScrollInterval);
    autoScrollInterval = null;
  }
};

const resumeAutoScroll = () => {
  if (document.visibilityState === "visible") {
    pauseAutoScroll();
    startAutoScroll();
  }
};

const handleIntersection = (entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      startAutoScroll();
    } else {
      pauseAutoScroll();
    }
  });
};

const handleVisibilityChange = () => {
  if (document.visibilityState === "hidden") {
    pauseAutoScroll();
  } else {
    resumeAutoScroll();
  }
};

onMounted(() => {
  observer = new IntersectionObserver(handleIntersection, {
    threshold: 0.3,
  });

  if (componentRef.value) {
    observer.observe(componentRef.value);
  }

  document.addEventListener("visibilitychange", handleVisibilityChange);
});

onUnmounted(() => {
  pauseAutoScroll();
  if (observer) {
    observer.disconnect();
  }
  document.removeEventListener("visibilitychange", handleVisibilityChange);
});
</script>

<style scoped>
.hide-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.hide-scrollbar::-webkit-scrollbar {
  display: none;
}
</style>