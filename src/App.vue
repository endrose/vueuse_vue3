<script setup lang="ts">
import { useColorMode, useDraggable } from '@vueuse/core'
import { UsaDraggle } from '@vueuse/core'
// import HelloWorld from './components/HelloWorld.vue'
import IconSun from '../src/components/IconSun.vue'
import IconMoon from '../src/components/IconMoon.vue'
import IconCoffe from '../src/components/IconCoffe.vue'
import { ref } from 'vue'

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
    "color": colorMode.value
  })
}

const elnoImportantTItle = ref(null)
const elimportantTitle = ref(null)
const elnotUrgentTItle = ref(null)
const elurgentFile = ref(null)

const { style: style1 } = useDraggable(elnoImportantTItle, {
  initialValue: { x: 40, y: 40, }
});

const { style: style2 } = useDraggable(elimportantTitle, {
  initialValue: { x: 60, y: 60, }
});

const { style: style3 } = useDraggable(elnotUrgentTItle, {
  initialValue: { x: 80, y: 80, }
});

const { style: style4 } = useDraggable(elurgentFile, {
  initialValue: { x: 100, y: 100, }
});


</script>

<template>
  <header style="
    height: 50px;
     align-items: center; 
     display: flex; 
     justify-content: space-between; 
     border-bottom: 1px solid #ccc;
     padding-bottom: 10px;
     ">
    <h1 style="font-size:1.2rem;">Build with Endros</h1>
    <button style="display: flex; align-items: center;" @click="switchTheme" class="btn btn- btn-block">
      <IconSun v-if="colorMode === 'light'" />
      <IconMoon v-else-if="colorMode === 'dark'" />
      <IconCoffe v-else />
    </button>
  </header>
  <main>
    <h2>Whiteboard Cansvas</h2>
    <div class="whiteboard">
      <div class="whiteboard-section">
        <h3 ref="elimportantTitle" :style="style1" style="position: fixed;">Important</h3>
      </div>
      <div class="whiteboard-section">
        <UseDraggable :initialValue="{ x: 10, y: 10 }">
          <h3 ref="elNotImportantTitle" :style="style2" style="position: fixed;">Not Impartant</h3>
        </UseDraggable>

      </div>
      <div class="whiteboard-section">
        <h3 ref="elurgentFile" :style="style3" style="position: fixed;">Urgent</h3>
      </div>
      <div class="whiteboard-section">
        <h3 ref="elnotUrgentTItle" :style="style4" style="position: fixed;">Not Urgent</h3>
      </div>
    </div>
  </main>
  <!-- <HelloWorld msg="Vite + Vue" /> -->
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

.cafe {
  filter: sepia(0.9) hue-rotate(315deg) brightness(0.9);
}

.whiteboard {

  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
}

.whiteboard-section {

  border: 1px solid #ccc;
  position: relative;
  min-height: 200px;
}


.dark {
  background-color: #222;
  color: #fff;
}
</style>
