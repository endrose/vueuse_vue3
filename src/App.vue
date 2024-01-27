<script setup lang="ts">
import { useColorMode } from '@vueuse/core'
import HelloWorld from './components/HelloWorld.vue'
import IconSun from '../src/components/IconSun.vue'
import IconMoon from '../src/components/IconMoon.vue'
import IconCoffe from '../src/components/IconCoffe.vue'

const colorMode = useColorMode(
  {
    modes: {
      cafe: 'cafe'
    }
  }
);



const switchTheme = () => {
  // colorMode.value = colorMode.value === 'dark' ? 'light' : 'dark'
  if (colorMode.value === 'dark') {
    colorMode.value = 'cafe'

  } else if (colorMode.value === 'cafe') {
    colorMode.value = 'light'
  } else {
    colorMode.value = 'dark'
  }
  console.log({
     "color":colorMode.value
  })
}

</script>

<template>
  <header style="height: 50px; align-items: center; display: flex; justify-content: space-between;">
    <h1 style="font-size:1.2rem;">Build with Endros</h1>
    <button style="display: flex; align-items: center;" @click="switchTheme" class="btn btn- btn-block">
      <IconSun v-if="colorMode === 'light'" />
      <IconMoon v-else-if="colorMode === 'dark'" />
      <IconCoffe v-else/>
    </button>
  </header>
  <h1>{{ colorMode }}</h1>

  <a href="https://vitejs.dev" target="_blank">
    <img src="/vite.svg" class="logo" alt="Vite logo" />
  </a>
  <a href="https://vuejs.org/" target="_blank">
    <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
  </a>
  <HelloWorld msg="Vite + Vue" />
</template>

<style>
/* .logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
} */

/* .logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
} */

.dark {
  background-color: #222;
  color: #fff;
}
</style>
