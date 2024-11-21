<template>
  <section class="relative isolate bg-white" id="contact" aria-labelledby="contact-heading">
    <div class="mx-auto grid max-w-7xl grid-cols-1 lg:grid-cols-2">
      <!-- Contact Info Section -->
      <div class="relative px-6 pb-20 pt-24 sm:pt-32 lg:static lg:px-8 lg:py-48">
        <div class="mx-auto max-w-xl lg:mx-0 lg:max-w-lg">
          <div 
            class="absolute inset-y-0 left-0 -z-10 w-full overflow-hidden bg-gray-100 ring-1 ring-gray-900/10 lg:w-1/2"
            aria-hidden="true"
          >
            <svg class="absolute inset-0 h-full w-full stroke-gray-200 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]" aria-hidden="true">
              <defs>
                <pattern id="83fd4e5a-9d52-42fc-97b6-718e5d7ee527" width="200" height="200" x="100%" y="-1" patternUnits="userSpaceOnUse">
                  <path d="M130 200V.5M.5 .5H200" fill="none" />
                </pattern>
              </defs>
              <rect width="100%" height="100%" stroke-width="0" fill="white" />
              <svg x="100%" y="-1" class="overflow-visible fill-gray-50">
                <path d="M-470.5 0h201v201h-201Z" stroke-width="0" />
              </svg>
              <rect width="100%" height="100%" stroke-width="0" fill="url(#83fd4e5a-9d52-42fc-97b6-718e5d7ee527)" />
            </svg>
          </div>
          <h2 id="contact-heading" class="text-pretty text-4xl font-semibold tracking-tight text-gray-900 sm:text-5xl">Contact Us</h2>
          <p class="mt-6 text-lg/8 text-gray-600">Ready to start your construction project? Contact Art's General Construction today for a consultation. We're here to turn your vision into reality with expert craftsmanship and professional service.</p>
          
          <dl class="mt-10 space-y-4 text-base/7 text-gray-600">
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Address</span>
                <BuildingOffice2Icon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>
                <address class="not-italic">
                  2535 Kettner Blvd, Suite #1A3<br />San Diego, CA 92101
                </address>
              </dd>
            </div>
            
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Email</span>
                <EnvelopeIcon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>
                <a 
                  class="hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2 rounded-sm"
                  href="mailto:info@artsgci.com"
                  aria-label="Send email to info@artsgci.com"
                >
                  info@artsgci.com
                </a>
              </dd>
            </div>
          </dl>
        </div>
      </div>

      <!-- Contact Form Section -->
      <form class="mt-5" aria-label="Contact form">
        <div class="mx-auto max-w-xl lg:mr-0 lg:max-w-lg">
          <BuildertrendContact />
        </div>
      </form>
    </div>
  </section>
</template>

<script setup>

import {
  PhoneIcon,
  BuildingOffice2Icon,
  EnvelopeIcon
} from "@heroicons/vue/24/outline";
import { ref } from 'vue';

const submitForm = () => {
  console.log("Submitting form..")

}
</script>