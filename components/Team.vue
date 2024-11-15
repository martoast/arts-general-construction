<template>
  <section class="bg-white relative overflow-hidden">
    <div class="mx-auto max-w-7xl px-6 py-24 sm:py-32 lg:px-8">
      <!-- Header -->
      <div class="relative z-10 max-w-2xl">
        <h2 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">Meet Our Founder</h2>
        <p class="mt-6 text-lg text-gray-600">Bringing architectural excellence and construction expertise to San Diego for over 15 years.</p>
      </div>

      <!-- Founder Content -->
      <div class="mt-16 grid gap-8 lg:grid-cols-2 lg:gap-16">
        <!-- Image Column -->
        <div class="relative aspect-[4/5] lg:aspect-auto lg:h-[640px]">
          <img 
            src="/arturo.jpg" 
            alt="Arturo Rodriguez - Founder"
            class="absolute inset-0 h-full w-full object-cover rounded-2xl shadow-xl"
          />
          <div class="absolute inset-0 rounded-2xl ring-1 ring-inset ring-gray-900/10"></div>
        </div>

        <!-- Info Column -->
        <div class="lg:pt-8">
          <div class="flex flex-col sm:flex-row sm:items-center gap-y-2 sm:gap-x-4">
            <h3 class="text-2xl font-bold text-gray-900">Arturo Rodriguez</h3>
            <div class="inline-flex self-start sm:self-auto text-sm font-medium text-red-600 border border-red-200 rounded-full px-3 py-1">
              Owner & Founder
            </div>
          </div>

          <!-- Credentials -->
          <div class="mt-8 space-y-6">
            <div>
              <h4 class="font-semibold text-gray-900">Education & Licensing</h4>
              <p class="mt-3 text-gray-600">Licensed Architect in Mexico | Construction Management Professional</p>
            </div>

            <!-- Bio -->
            <div>
              <h4 class="font-semibold text-gray-900">Professional Journey</h4>
              <p class="mt-3 text-gray-600">{{ bio }}</p>
            </div>

            <!-- Contact -->
            <div class="pt-8">
              <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-4 sm:gap-x-6">
                <a 
                  href="mailto:info@artsgci.com"
                  class="rounded-md bg-red-600 px-6 py-3 text-sm font-semibold text-white shadow-sm hover:bg-red-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-red-600 text-center"
                >
                  Get in Touch
                </a>
                <a 
                  :href="linkedinUrl"
                  target="_blank"
                  class="text-sm font-semibold leading-6 text-gray-900 hover:text-red-600 text-center sm:text-left"
                >
                  Connect on LinkedIn <span aria-hidden="true">→</span>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const bio = `Arturo Rodriguez founded Art's General Construction in 2008, bringing his architectural expertise from Mexico to the Bay Area. His journey began as a licensed architect in Mexico, where he honed his skills in both design and construction management.

With over 15 years of experience in the U.S. construction industry, Arturo has built a reputation for delivering exceptional quality and innovative solutions. His architectural background gives him a unique perspective on construction projects, allowing him to bridge the gap between design vision and practical implementation.

Under his leadership, Art's General Construction has grown into a trusted name in San Diego, known for its commitment to quality, attention to detail, and customer satisfaction. Arturo personally oversees major projects, ensuring that each one meets his high standards of excellence.`

const linkedinUrl = 'https://www.linkedin.com/company/artsgeneralconstruction/?trk=ppro_cprof' // Replace with actual LinkedIn URL
</script>