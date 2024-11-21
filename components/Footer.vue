<template>
  <footer class="bg-white" role="contentinfo" aria-label="Site footer">
    <div class="mx-auto max-w-7xl px-6 pb-8 pt-16 sm:pt-24 lg:px-8 lg:pt-32">
      <div class="xl:grid xl:grid-cols-3 xl:gap-8">
        <!-- Logo and Company Info -->
        <div class="flex flex-col items-center sm:items-start">
          <img
            src="/Artslogo.png"
            alt="Art's General Construction"
            width="200"
            height="200"
            class="mx-auto sm:mx-0"
          />

          <div class="flex justify-center sm:justify-start gap-x-6 mt-4 w-full">
            <a
              v-for="item in navigation.social"
              :key="item.name"
              target="_blank"
              :href="item.href"
              class="text-gray-600 hover:text-gray-800 p-2 rounded-full focus:outline-none focus:ring-2 focus:ring-red-500 ml-0 md:ml-2"
              :aria-label="`Visit our ${item.name} page`"
            >
              <component :is="item.icon" class="h-6 w-6" aria-hidden="true" />
            </a>
          </div>
        </div>

        <!-- Navigation Grid -->
        <nav
          class="mt-16 grid grid-cols-2 gap-8 xl:col-span-2 xl:mt-0"
          aria-label="Footer navigation"
        >
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <!-- Services Column 1 -->
            <div>
              <h3
                id="footer-services-1"
                class="text-sm/6 font-semibold text-gray-900"
              >
                Services
              </h3>
              <ul
                role="list"
                class="mt-6 space-y-4"
                aria-labelledby="footer-services-1"
              >
                <li v-for="service in services.slice(0, 3)" :key="service.name">
                  <a
                    :href="service.href"
                    class="text-sm/6 text-gray-600 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-red-500 rounded-sm p-1"
                  >
                    {{ service.name }}
                  </a>
                </li>
              </ul>
            </div>
            <!-- Services Column 2 -->
            <div class="mt-10 md:mt-0">
              <h3
                id="footer-services-2"
                class="text-sm/6 font-semibold text-gray-900"
              >
                More Services
              </h3>
              <ul
                role="list"
                class="mt-6 space-y-4"
                aria-labelledby="footer-services-2"
              >
                <li v-for="service in services.slice(3)" :key="service.name">
                  <a
                    :href="service.href"
                    class="text-sm/6 text-gray-600 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-red-500 rounded-sm p-1"
                  >
                    {{ service.name }}
                  </a>
                </li>
              </ul>
            </div>
          </div>

          <div class="md:grid md:grid-cols-2 md:gap-8">
            <!-- Company Links -->
            <div>
              <h3
                id="footer-company"
                class="text-sm/6 font-semibold text-gray-900"
              >
                Company
              </h3>
              <ul
                role="list"
                class="mt-6 space-y-4"
                aria-labelledby="footer-company"
              >
                <li v-for="item in navigation.company" :key="item.name">
                  <a
                    :href="item.href"
                    class="text-sm/6 text-gray-600 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-red-500 rounded-sm p-1"
                  >
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
            <!-- Legal Links -->
            <div class="mt-10 md:mt-0">
              <h3
                id="footer-legal"
                class="text-sm/6 font-semibold text-gray-900"
              >
                Legal
              </h3>
              <ul
                role="list"
                class="mt-6 space-y-4"
                aria-labelledby="footer-legal"
              >
                <li v-for="item in navigation.legal" :key="item.name">
                  <a
                    :href="item.href"
                    target="_blank"
                    class="text-sm/6 text-gray-600 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-red-500 rounded-sm p-1"
                    :aria-label="`${item.name} (opens in new tab)`"
                  >
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </nav>
      </div>

      <!-- Copyright -->
      <div class="mt-16 border-t border-gray-900/10 pt-8 sm:mt-20 lg:mt-24">
        <p class="text-sm/6 text-gray-600">
          &copy; {{ new Date().getFullYear() }} Art's General Construction, Inc.
          All rights reserved.
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { defineComponent, h } from "vue";

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
    name: "ADU's",
    href: "#adus",
  },
  {
    name: "Outdoor Living Spaces",
    href: "#services",
  },
  {
    name: "Project Management",
    href: "#services",
  },
];

const navigation = {
  company: [
    { name: "About", href: "#about" },
    { name: "Contact", href: "#contact" },
  ],
  legal: [
    { name: "Privacy", href: "/privacy-policy" },
    { name: "Terms", href: "/terms-of-service" },
  ],
  social: [
    {
      name: "Facebook",
      href: "https://www.facebook.com/p/Arts-General-Construction-100032105995800/?_rdr",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d: "M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
    },
    {
      name: "Instagram",
      href: "#",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d: "M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
    },
    {
      name: "LinkedIn",
      href: "https://www.linkedin.com/company/artsgeneralconstruction/",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d: "M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
    },
  ],
};
</script>
