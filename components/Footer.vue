<template>
  <footer class="bg-white">
    <div class="mx-auto max-w-7xl px-6 pb-8 pt-16 sm:pt-24 lg:px-8 lg:pt-32">
      <div class="xl:grid xl:grid-cols-3 xl:gap-8">
        <!-- Logo and Company Info Section -->
        <div class="space-y-8">
          <img class="h-12" src="/logo.png" alt="Art's General Construction" />
          <p class="text-balance text-sm/6 text-gray-600">
            San Diego's trusted name in construction since 2008. We transform visions into reality with quality craftsmanship and attention to detail.
          </p>
          <div class="flex gap-x-6">
            <a v-for="item in navigation.social" :key="item.name" :href="item.href" class="text-gray-600 hover:text-gray-800">
              <span class="sr-only">{{ item.name }}</span>
              <component :is="item.icon" class="h-6 w-6" aria-hidden="true" />
            </a>
          </div>
        </div>

        <!-- Services and Links Grid -->
        <div class="mt-16 grid grid-cols-2 gap-8 xl:col-span-2 xl:mt-0">
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h3 class="text-sm/6 font-semibold text-gray-900">Services</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="service in services.slice(0, 3)" :key="service.name">
                  <a :href="service.href" class="text-sm/6 text-gray-600 hover:text-gray-900">{{ service.name }}</a>
                </li>
              </ul>
            </div>
            <div class="mt-10 md:mt-0">
              <h3 class="text-sm/6 font-semibold text-gray-900">More Services</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="service in services.slice(3)" :key="service.name">
                  <a :href="service.href" class="text-sm/6 text-gray-600 hover:text-gray-900">{{ service.name }}</a>
                </li>
              </ul>
            </div>
          </div>
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h3 class="text-sm/6 font-semibold text-gray-900">Company</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="item in navigation.company" :key="item.name">
                  <a :href="item.href" class="text-sm/6 text-gray-600 hover:text-gray-900">{{ item.name }}</a>
                </li>
              </ul>
            </div>
            <div class="mt-10 md:mt-0">
              <h3 class="text-sm/6 font-semibold text-gray-900">Legal</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="item in navigation.legal" :key="item.name">
                  <a :href="item.href" class="text-sm/6 text-gray-600 hover:text-gray-900">{{ item.name }}</a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <!-- Copyright -->
      <div class="mt-16 border-t border-gray-900/10 pt-8 sm:mt-20 lg:mt-24">
        <p class="text-sm/6 text-gray-600">&copy; 2024 Art's General Construction, Inc. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { defineComponent, h } from 'vue'

const services = [
  {
    name: "Custom Home Building",
    href: "#services",
  },
  {
    name: "Home Renovation",
    href: "#services",
  },
  {
    name: "Additions and Extensions",
    href: "#services",
  },
  {
    name: "Outdoor Living Spaces",
    href: "#services",
  },
  {
    name: "Project Management",
    href: "#services",
  },
]

const navigation = {
  company: [
    { name: 'About', href: '#about' },
    { name: 'Contact', href: '#contact' },
    { name: 'Testimonials', href: '#testimonials' },
  ],
  legal: [
    { name: 'Privacy', href: '#privacy' },
    { name: 'Terms', href: '#terms' },
  ],
  social: [
    {
      name: 'Facebook',
      href: '#',
      icon: defineComponent({
        render: () =>
          h('svg', { fill: 'currentColor', viewBox: '0 0 24 24' }, [
            h('path', {
              'fill-rule': 'evenodd',
              d: 'M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z',
              'clip-rule': 'evenodd',
            }),
          ]),
      }),
    },
    // ... rest of social icons remain the same
  ],
}
</script>