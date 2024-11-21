<template>
  <div class="bg-white min-h-screen">
    <main class="max-w-4xl mx-auto px-6 py-12">
      <nav aria-label="Back navigation">
        <a 
          href="/" 
          class="inline-flex items-center text-gray-600 hover:text-gray-900 mb-8 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2 rounded-md p-2"
          aria-label="Return to homepage"
        >
          <svg 
            xmlns="http://www.w3.org/2000/svg" 
            class="h-5 w-5 mr-2" 
            viewBox="0 0 20 20" 
            fill="currentColor"
            aria-hidden="true"
          >
            <path fill-rule="evenodd" d="M9.707 16.707a1 1 0 01-1.414 0l-6-6a1 1 0 010-1.414l6-6a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l4.293 4.293a1 1 0 010 1.414z" clip-rule="evenodd" />
          </svg>
          Back to Home
        </a>
      </nav>

      <article class="bg-gray-50 rounded-lg shadow-sm border border-gray-200 p-8">
        <h1 class="text-3xl font-bold text-gray-900 mb-6">Privacy Policy</h1>
        
        <div class="space-y-8 text-gray-600">
          <p class="text-sm text-gray-500" aria-label="Last update date">Last Updated: 11/11/2024</p>
          
          <div class="prose prose-gray max-w-none">
            <section aria-labelledby="collection-heading">
              <h2 id="collection-heading" class="text-xl font-semibold text-gray-900 mt-8 mb-4">Information Collection</h2>
              <p>When you submit our contact form, we collect:</p>
              <ul role="list" class="mt-4 space-y-3">
                <li class="flex items-start">
                  <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                  <span>Your name, email address, and phone number</span>
                </li>
                <li class="flex items-start">
                  <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                  <span>Any additional information you provide about your project</span>
                </li>
              </ul>
            </section>

            <section aria-labelledby="usage-heading">
              <h2 id="usage-heading" class="text-xl font-semibold text-gray-900 mt-8 mb-4">How We Use Your Information</h2>
              <ul role="list" class="mt-4 space-y-3">
                <li class="flex items-start">
                  <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                  <span>To respond to your inquiries</span>
                </li>
                <li class="flex items-start">
                  <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                  <span>To provide requested information about our services</span>
                </li>
                <li class="flex items-start">
                  <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                  <span>To improve our website and services</span>
                </li>
              </ul>
            </section>

            <section aria-labelledby="security-heading">
              <h2 id="security-heading" class="text-xl font-semibold text-gray-900 mt-8 mb-4">Information Security</h2>
              <p>We implement appropriate security measures to protect your information. Your data is encrypted and stored securely.</p>
            </section>

            <section aria-labelledby="contact-heading">
              <h2 id="contact-heading" class="text-xl font-semibold text-gray-900 mt-8 mb-4">Contact Us</h2>
              <p>For privacy-related questions, contact us at:</p>
            </section>
          </div>

          <address class="mt-8 pt-6 border-t border-gray-200 not-italic">
            <div class="text-sm text-gray-500">
              Art's General Construction<br>
              2535 Kettner Blvd, Suite #1A 3<br>
              San Diego, CA 92101<br>
              <a 
                href="mailto:info@artsgci.com" 
                class="text-blue-600 hover:text-blue-800 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2 rounded-sm"
                aria-label="Email us at info@artsgci.com"
              >
                info@artsgci.com
              </a>
            </div>
          </address>
        </div>
      </article>
    </main>
  </div>
</template>