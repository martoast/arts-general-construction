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
        <h1 class="text-3xl font-bold text-gray-900 mb-6">Terms of Service</h1>
        
        <div class="space-y-6 text-gray-600">
          <p class="text-sm text-gray-500" aria-label="Last update date">Last Updated: 11/11/2024</p>
          
          <div class="prose prose-gray max-w-none">
            <p class="text-lg">By using this contact form and website, you agree to these terms:</p>
            
            <ul role="list" class="mt-4 space-y-3 list-none">
              <li class="flex items-start">
                <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                <span>You will provide accurate and truthful information when contacting us</span>
              </li>
              <li class="flex items-start">
                <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                <span>We may use your contact information to respond to your inquiry</span>
              </li>
              <li class="flex items-start">
                <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                <span>We are not liable for any damages related to your use of this website</span>
              </li>
              <li class="flex items-start">
                <span class="flex-shrink-0 h-6 w-6 text-blue-600 mr-2" aria-hidden="true">•</span>
                <span>This website is provided "as is" without warranties of any kind</span>
              </li>
            </ul>
          </div>

          <div class="mt-8 pt-6 border-t border-gray-200">
            <p class="mb-4">
              For questions about these terms, contact us at 
              <a 
                href="mailto:info@artsgci.com" 
                class="text-blue-600 hover:text-blue-800 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2 rounded-sm"
                aria-label="Email us at info@artsgci.com"
              >
                info@artsgci.com
              </a>
            </p>
            
            <address class="text-sm text-gray-500 not-italic">
              Art's General Construction<br>
              2535 Kettner Blvd, Suite #1A 3<br>
              San Diego, CA 92101
            </address>
          </div>
        </div>
      </article>
    </main>
  </div>
</template>