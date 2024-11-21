<!-- components/BuildertrendContact.vue -->
<template>
  <div class="relative min-h-[400px]" role="region" aria-label="Contact form">
    <!-- Loading State -->
    <div
      v-if="loading"
      class="absolute inset-0 flex items-center justify-center bg-gray-50"
      role="status"
      aria-live="polite"
    >
      <div class="flex flex-col items-center gap-4">
        <div
          class="h-8 w-8 animate-spin rounded-full border-4 border-gray-200 border-t-blue-500"
          aria-hidden="true"
        ></div>
        <p class="text-gray-600">Loading form...</p>
      </div>
    </div>

    <!-- Error State -->
    <div
      v-if="error"
      class="absolute inset-0 flex items-center justify-center bg-gray-50"
      role="alert"
    >
      <div class="flex flex-col items-center gap-4 p-4 text-center">
        <div class="rounded-full bg-red-100 p-4" aria-hidden="true">
          <svg
            class="h-6 w-6 text-red-600"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
            />
          </svg>
        </div>
        <p class="text-red-600">{{ error }}</p>
        <button
          @click="retryLoading"
          class="rounded bg-blue-500 px-4 py-2 text-white hover:bg-blue-600 min-h-[44px]"
        >
          Retry loading form
        </button>
      </div>
    </div>

    <!-- Buildertrend Form -->
    <div v-if="mounted && !loading && !error">
      <iframe
        src="https://buildertrend.net/leads/contactforms/ContactFormFrame.aspx?builderID=84107"
        scrolling="no"
        id="btIframe"
        title="Art's General Construction Contact Form"
        class="mx-auto w-full border-0 bg-transparent"
        :style="{ height: iframeHeight + 'px' }"
      ></iframe>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const mounted = ref(false);
const loading = ref(true);
const error = ref(null);
const iframeHeight = ref(600); // Default height

// Script loading function
const loadBuilderTrendScript = () => {
  return new Promise((resolve, reject) => {
    // Check if script is already loaded
    if (document.querySelector('script[src*="btClientContactForm.js"]')) {
      resolve();
      return;
    }

    const script = document.createElement("script");
    script.src =
      "https://buildertrend.net/leads/contactforms/js/btClientContactForm.js";
    script.type = "text/javascript";
    script.async = true;

    script.onload = () => resolve();
    script.onerror = () => reject(new Error("Failed to load contact form"));

    document.head.appendChild(script);
  });
};

// Retry loading function
const retryLoading = async () => {
  error.value = null;
  loading.value = true;
  await initializeForm();
};

// Message handler for iframe resizing
const handleMessage = (event) => {
  if (event.origin === "https://buildertrend.net") {
    try {
      const data = JSON.parse(event.data);
      if (data.frameHeight) {
        iframeHeight.value = data.frameHeight;
      }
    } catch (e) {
      console.warn("Invalid message data:", e);
    }
  }
};

// Initialize form
const initializeForm = async () => {
  try {
    await loadBuilderTrendScript();
    mounted.value = true;
    loading.value = false;
  } catch (err) {
    error.value = "Unable to load the contact form. Please try again.";
    loading.value = false;
  }
};

// Lifecycle hooks
onMounted(() => {
  initializeForm();
  window.addEventListener("message", handleMessage);
});

onUnmounted(() => {
  window.removeEventListener("message", handleMessage);
});
</script>
