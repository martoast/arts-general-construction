<template>
  <div class="bg-white">
    <div class="mx-auto max-w-2xl px-4 py-24 sm:px-6 sm:py-32 lg:max-w-7xl lg:px-8">
      <!-- Header - Updated to match design -->
      <div>
        <h2 class="font-medium text-red-600">About Our Leadership</h2>
        <p class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">
          Meet Our Founder
        </p>
      </div>

      <!-- Founder Content -->
      <div class="mt-8 sm:mt-16 grid gap-8 lg:grid-cols-2 lg:gap-16">
        <!-- Image Column - Simplified -->
        <div class="relative w-full max-w-2xl lg:max-w-none mx-auto">
          <div class="relative aspect-[5/4] w-full" style="max-height: 400px;">
            <img 
              src="/arturo.jpg" 
              alt="Arturo Rodriguez - Founder"
              class="absolute inset-0 h-full w-full object-cover rounded-xl sm:rounded-2xl shadow-xl"
            />
            <div class="absolute inset-0 rounded-xl sm:rounded-2xl ring-1 ring-inset ring-gray-900/10"></div>
          </div>
        </div>

        <!-- Info Column -->
        <div class="lg:pt-8">
          <div class="flex flex-col sm:flex-row sm:items-center gap-y-2 sm:gap-x-4">
            <h3 class="text-xl sm:text-2xl font-bold text-gray-900">Arturo Rodriguez</h3>
            <div class="inline-flex self-start sm:self-auto text-sm font-medium text-red-600 border border-red-200 rounded-full px-3 py-1">
              Owner & Founder
            </div>
          </div>

          <!-- Credentials -->
          <div class="mt-6 sm:mt-8 space-y-6">
            <div>
              <h4 class="text-base font-semibold text-gray-900">Education & Licensing</h4>
              <p class="mt-2 sm:mt-3 text-sm sm:text-base text-gray-600">Licensed Architect in Mexico | Construction Management Professional</p>
            </div>

            <!-- Bio -->
            <div>
              <h4 class="text-base font-semibold text-gray-900">Professional Journey</h4>
              <p class="mt-2 sm:mt-3 text-sm sm:text-base text-gray-600">{{ bio }}</p>
            </div>

            <!-- Contact -->
            <div class="pt-6 sm:pt-8">
              <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-4 sm:gap-x-6">
                <a 
                  href="mailto:info@artsgci.com"
                  class="rounded-md bg-red-600 px-4 sm:px-6 py-2.5 sm:py-3 text-sm font-semibold text-white shadow-sm hover:bg-red-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-red-600 text-center transition-colors"
                >
                  Get in Touch
                </a>
                <a 
                  :href="linkedinUrl"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-sm font-semibold leading-6 text-gray-900 hover:text-red-600 text-center sm:text-left transition-colors"
                >
                  Connect on LinkedIn <span aria-hidden="true" class="ml-1">→</span>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const bio = `As founder of Art's General Construction since 2008, Arturo Rodriguez brings over 15 years of U.S. construction expertise combined with his background as a licensed architect from Mexico. His unique perspective bridges design vision and practical implementation, leading to innovative solutions for every project. Under his leadership, Art's General Construction has become synonymous with quality and excellence in San Diego.`

const linkedinUrl = 'https://www.linkedin.com/company/artsgeneralconstruction/?trk=ppro_cprof'
</script>