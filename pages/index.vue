<template>
    <div>
      <Hero/>
      <About id="about"/>
      
      <Services id="services"/>
      <ADU id="adus"/>
      <Team/>
      <!-- <Testimonials/> -->
      <Contact id="contact"/>
      <Footer/>
    </div>
  </template>


<script setup>

useHead({
  htmlAttrs: {
    lang: 'en',
  }
})

useSeoMeta({
        robots: 'index, follow',
        title: "Art's General Construction",
        ogTitle: "Art's General Construction",
    
        author: 'Alex Martos',
        charset: 'utf-8',
    
        description: "From custom homes to complete renovations, we bring exceptional craftsmanship and dedicated service to every project.",
        ogDescription: "From custom homes to complete renovations, we bring exceptional craftsmanship and dedicated service to every project.",
        
        appleMobileWebAppCapable: 'yes',
        mobileWebAppCapable: 'yes',
    
        ogImage: '/logo.png',
    
        ogLocaleAlternate: ['es_LA'],
        ogType: 'website',
        viewport: 'width=device-width, initial-scale=1',
    })


</script>

  