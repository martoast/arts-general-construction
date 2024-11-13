<template>
    <div class="bg-white py-24 sm:py-32">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-2xl sm:text-center">
          <h2 class="text-3xl font-semibold tracking-tight text-gray-900 sm:text-5xl">Leadership & Expertise</h2>
          <p class="mt-6 text-lg/8 text-gray-600">
            With over 15 years of excellence in the Bay Area, our leadership brings international expertise and a passion for transforming spaces through innovative design and quality construction.
          </p>
        </div>
        <ul role="list" class="mx-auto mt-20 grid max-w-2xl grid-cols-1 gap-x-6 gap-y-20 sm:grid-cols-2 lg:max-w-4xl lg:gap-x-8 xl:max-w-none">
          <li v-for="person in people" :key="person.name" class="flex flex-col gap-6 xl:flex-row">
            <img 
              class="aspect-[4/5] w-52 flex-none rounded-2xl object-cover cursor-pointer hover:opacity-90 transition-opacity" 
              :src="person.imageUrl" 
              :alt="`Portrait of ${person.name}`"
              @click="openModal(person)" 
            />
            <div class="flex-auto">
              <div class="flex items-center gap-x-4">
                <h3 class="text-lg font-semibold tracking-tight text-gray-900">{{ person.name }}</h3>
                <div class="text-sm text-red-600 border border-red-200 rounded-full px-3 py-1">
                  {{ person.role }}
                </div>
              </div>
              <div class="mt-4">
                <h4 class="text-sm font-medium text-gray-900">Education & Background</h4>
                <p class="mt-2 text-sm text-gray-500">{{ person.education }}</p>
              </div>
              <div class="mt-4">
                <h4 class="text-sm font-medium text-gray-900">Professional Journey</h4>
                <p class="mt-2 text-base text-gray-600">{{ person.bio }}</p>
              </div>
              <div class="mt-6 flex gap-x-4">
                <a v-if="person.linkedin" :href="person.linkedin" target="_blank" class="text-gray-400 hover:text-gray-500">
                  <span class="sr-only">LinkedIn</span>
                  <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                  </svg>
                </a>
                <a v-if="person.email" :href="`mailto:${person.email}`" class="text-gray-400 hover:text-gray-500">
                  <span class="sr-only">Email</span>
                  <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                  </svg>
                </a>
              </div>
            </div>
          </li>
        </ul>
      </div>
  
      <!-- Bio Modal -->
      <div v-if="selectedPerson" class="fixed inset-0 z-50 overflow-y-auto" @click="closeModal">
        <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
          <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" aria-hidden="true"></div>
          <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
          <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-2xl sm:w-full" @click.stop>
            <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
              <div class="sm:flex sm:items-start">
                <div class="mt-3 text-center sm:mt-0 sm:text-left w-full">
                  <h3 class="text-lg leading-6 font-medium text-gray-900">
                    About {{ selectedPerson.name }}
                  </h3>
                  <div class="mt-4">
                    <img 
                      :src="selectedPerson.imageUrl" 
                      :alt="`Portrait of ${selectedPerson.name}`"
                      class="w-full h-64 object-cover rounded-lg mb-4"
                    />
                    <p class="text-sm text-gray-500">{{ selectedPerson.fullBio || selectedPerson.bio }}</p>
                  </div>
                </div>
              </div>
            </div>
            <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
              <button 
                type="button" 
                class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm"
                @click="closeModal"
              >
                Close
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const selectedPerson = ref(null);
  
  const people = [
    {
      name: 'Arturo Rodriguez',
      role: 'Owner & Founder',
      imageUrl: '/arturo-profile.jpg', // You'll need to replace with actual image path
      education: 'Licensed Architect in Mexico | Construction Management Professional',
      bio: "Since founding Art's General Construction in 2008, Arturo has been transforming the Bay Area's construction landscape with his unique blend of architectural expertise and hands-on construction knowledge.",
      fullBio: `Arturo Rodriguez founded Art's General Construction in 2008, bringing his architectural expertise from Mexico to the Bay Area. His journey began as a licensed architect in Mexico, where he honed his skills in both design and construction management. 
  
  With over 15 years of experience in the U.S. construction industry, Arturo has built a reputation for delivering exceptional quality and innovative solutions. His architectural background gives him a unique perspective on construction projects, allowing him to bridge the gap between design vision and practical implementation.
  
  Under his leadership, Art's General Construction has grown into a trusted name in the Bay Area, known for its commitment to quality, attention to detail, and customer satisfaction. Arturo personally oversees major projects, ensuring that each one meets his high standards of excellence.`,
      email: 'arturo@artsgeneralconstruction.com',
      linkedin: '#', // Replace with actual LinkedIn profile URL if available
    },
    {
      name: 'Maria Rodriguez',
      role: 'Operations Director',
      imageUrl: '/maria-profile.jpg', // You'll need to replace with actual image path
      education: 'Business Administration | Project Management Professional (PMP)',
      bio: 'Leading our day-to-day operations, Maria ensures seamless project execution and customer satisfaction through effective team coordination and resource management.',
      fullBio: `Maria Rodriguez brings over a decade of experience in construction project management and business operations. Her expertise in coordinating complex projects and managing client relationships has been instrumental in the company's growth and success.
  
  As Operations Director, Maria oversees all aspects of project execution, from initial planning to final delivery. Her attention to detail and commitment to excellence ensure that each project meets our high standards of quality while staying on schedule and within budget.
  
  Maria's leadership has been crucial in developing and implementing efficient systems and processes that have streamlined our operations and improved customer satisfaction.`,
      email: 'maria@artsgeneralconstruction.com',
      linkedin: '#', // Replace with actual LinkedIn profile URL if available
    }
  ];
  
  function openModal(person) {
    selectedPerson.value = person;
  }
  
  function closeModal() {
    selectedPerson.value = null;
  }
  </script>