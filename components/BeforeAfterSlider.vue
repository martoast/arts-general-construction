<template>
    <div class="relative w-full aspect-video overflow-hidden">
      <img
        :src="beforeImage"
        alt="Before"
        class="absolute top-0 left-0 w-full h-full object-cover"
        @error="handleImageError"
      />
      
      <div 
        class="absolute top-0 left-0 h-full w-full"
        :style="{ clipPath: `polygon(0 0, ${sliderPosition}% 0, ${sliderPosition}% 100%, 0 100%)` }"
      >
        <img
          :src="afterImage"
          alt="After"
          class="w-full h-full object-cover"
          @error="handleImageError"
        />
      </div>
  
      <div
        class="absolute top-0 bottom-0 w-1 bg-white cursor-ew-resize z-10"
        :style="{ left: `${sliderPosition}%` }"
        @mousedown.prevent="startDragging"
        @touchstart.prevent="startDragging"
      >
        <div class="absolute top-1/2 -translate-y-1/2 -translate-x-1/2 w-8 h-8 bg-white rounded-full shadow-lg flex items-center justify-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </div>
      </div>
  
      <div 
        class="absolute top-4 left-4 bg-black/50 text-white px-2 py-1 rounded transition-opacity duration-300"
        :class="{'opacity-0': sliderPosition <= 5, 'opacity-100': sliderPosition > 5}"
      >
        Before
      </div>
      <div 
        class="absolute top-4 right-4 bg-black/50 text-white px-2 py-1 rounded transition-opacity duration-300"
        :class="{'opacity-0': sliderPosition >= 95, 'opacity-100': sliderPosition < 95}"
      >
        After
      </div>
    </div>
 </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue'
  
  const props = defineProps({
    beforeImage: {
      type: String,
      required: true
    },
    afterImage: {
      type: String,
      required: true
    }
  })
  
  const sliderPosition = ref(50)
  let isDragging = false
  
  const handleImageError = (e) => {
    console.error('Image failed to load:', e.target.src)
  }
 
  const startDragging = (event) => {
    event.preventDefault()
    isDragging = true
    document.addEventListener('mousemove', handleDrag)
    document.addEventListener('touchmove', handleDrag)
    document.addEventListener('mouseup', stopDragging)
    document.addEventListener('touchend', stopDragging)
  }
  
  const handleDrag = (event) => {
    if (!isDragging) return
  
    const container = event.target.closest('.relative')
    const rect = container.getBoundingClientRect()
    const x = (event.type === 'touchmove' ? event.touches[0].clientX : event.clientX) - rect.left
    
    sliderPosition.value = Math.min(Math.max((x / rect.width) * 100, 0), 100)
  }
  
  const stopDragging = () => {
    isDragging = false
    document.removeEventListener('mousemove', handleDrag)
    document.removeEventListener('touchmove', handleDrag)
    document.removeEventListener('mouseup', stopDragging)
    document.removeEventListener('touchend', stopDragging)
  }
  
  onUnmounted(() => {
    document.removeEventListener('mousemove', handleDrag)
    document.removeEventListener('touchmove', handleDrag)
    document.removeEventListener('mouseup', stopDragging)
    document.removeEventListener('touchend', stopDragging)
  })
  </script>