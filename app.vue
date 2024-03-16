<template>
  <div class="app" :class="{ show: show }">
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
    link: [
      { rel: 'preload', href: '/background.jpeg', as: 'image' },
      { rel: 'preload', href: '/envelope-front-gold.jpeg', as: 'image' },
      { rel: 'preload', href: '/envelope-back-gold.webp', as: 'image' },
      { rel: 'preload', href: '/flap-shadow.webp', as: 'image' },
      { rel: 'preload', href: '/envelope-back-gold.png', as: 'image' },
      { rel: 'preload', href: '/envelope-outside-gold.png', as: 'image' },
      { rel: 'preload', href: '/envelope-gold.png', as: 'image' },
      { rel: 'preload', href: '/letter_blank.png', as: 'image' },
    ]
  };
});


const flip = ref(false)
const open = ref(false)
const exit = ref(false)
const show = ref(false)
const flipEnvelope = () => {
  flip.value = true;
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

onMounted(() => {
  setTimeout(() => {
    show.value = true;
    setTimeout(() => { flipEnvelope() }, 1000);
  }, 1000);
})
</script>
