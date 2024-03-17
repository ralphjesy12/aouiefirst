<template>
  <div class="app" :class="{ show: show }">
    <audio loop id="audio">
      <source src="/awemaweh.webm" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>

    <div class="envelope" :class="{ flip: flip, open: open, exit: exit }">
      <div class="envelope-flap"></div>
      <div class="envelope-flap-inner"></div>
      <div class="envelope-front-inner"></div>
      <div class="envelope-content">
        <img prefetch src="/letter.svg" width="100%" height="auto">
        <img prefetch src="/letter_02.svg" width="100%" height="auto">
        <div class="letter">
          <RsvpForm></RsvpForm>
        </div>
        <img prefetch src="/letter_05.svg" width="100%" height="auto">
        <div class="letter">
          <GiftRegistry></GiftRegistry>
        </div>
        <img prefetch src="/letter_08.svg" width="100%" height="auto">
      </div>
      <div class="envelope-front"></div>
      <div class="envelope-flap-shadow"></div>
      <div class="envelope-back"></div>
    </div>
  </div>
</template>

<script setup>
import RsvpForm from "./components/RsvpForm"
import GiftRegistry from "./components/GiftRegistry"


useHead(() => {
  return {
    title: 'You are invited!',
    meta: [
      { name: 'title', content: 'You are invited!' },
      { name: 'description', content: 'Hello, I am John Aouie. We are excited to see you all!' },
      // Open Graph / Facebook
      { property: 'og:type', content: 'website' },
      { property: 'og:url', content: 'https://aouie.baby/' },
      { property: 'og:title', content: 'You are invited!' },
      { property: 'og:description', content: 'Hello, I am John Aouie. We are excited to see you all!' },
      { property: 'og:image', content: 'https://aouie.baby/social.png' },
      // Twitter
      { property: 'twitter:card', content: 'summary_large_image' },
      { property: 'twitter:url', content: 'https://aouie.baby/' },
      { property: 'twitter:title', content: 'You are invited!' },
      { property: 'twitter:description', content: 'Hello, I am John Aouie. We are excited to see you all!' },
      { property: 'twitter:image', content: 'https://aouie.baby/social.png' }
    ],
    link: [
      { rel: 'preload', href: '/background.jpeg', as: 'image' },
      { rel: 'preload', href: '/envelope-front-gold.jpeg', as: 'image' },
      { rel: 'preload', href: '/envelope-back-gold.webp', as: 'image' },
      { rel: 'preload', href: '/flap-shadow.webp', as: 'image' },
      { rel: 'preload', href: '/envelope-back-gold.png', as: 'image' },
      { rel: 'preload', href: '/envelope-outside-gold.png', as: 'image' },
      { rel: 'preload', href: '/envelope-gold.png', as: 'image' },
      { rel: 'preload', href: '/letter_blank.png', as: 'image' },
      { rel: 'apple-touch-icon', sizes: '180x180', href: '/apple-touch-icon.png' },
      { rel: 'icon', type: 'image/png', sizes: '32x32', href: '/favicon-32x32.png' },
      { rel: 'icon', type: 'image/png', sizes: '16x16', href: '/favicon-16x16.png' },
      { rel: 'manifest', href: '/site.webmanifest' }
    ]
  };
});


const flip = ref(false)
const open = ref(false)
const exit = ref(false)
const show = ref(false)
const flipEnvelope = () => {
  flip.value = true;
  playAudio();
  setTimeout(() => {
    openEnvelope();
  }, 1000);
}

const openEnvelope = (event) => {
  open.value = true;
  setTimeout(() => {
    exit.value = true;
    
    setTimeout(() => {
      document.querySelector('body').style.overflowY = 'auto';
    }, 1000);
  }, 1500);
}

const playAudio = () => {
  var audio = document.getElementById("audio");
  audio.play();
}

onMounted(() => {
  setTimeout(() => {
    show.value = true;
    setTimeout(() => { flipEnvelope() }, 1000);
  }, 1000);
})
</script>
