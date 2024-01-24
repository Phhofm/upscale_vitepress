---
title: Selftrained
description: Visual Comparison of Multiple Self trained or interpolated Models
layout: doc
outline: [2, 4]
---

<script setup lang="ts">
  import imageCompare from "vue-image-compare2";
  import ImageSlider from './imageslider.vue' // the vue image slider example comparison component
  import cutoutfiles from './filelists/selftrained/cutout.json'
    import cutoutfiles_selection from './filelists/selftrained/cutout_selection.json'

//HTML5 Fullscreen API
const fullscreenEnabled = document.fullscreenEnabled; //check if fullscreen is possible
function enterFullscreen(elementName) {
  var element = document.getElementById(elementName);
  if(element.requestFullscreen) {
    element.requestFullscreen();
  } else if(element.msRequestFullscreen) {      // for IE11 (remove June 15, 2022)
    element.msRequestFullscreen();
  } else if(element.webkitRequestFullscreen) {  // iOS Safari
    element.webkitRequestFullscreen();
  }
}

// reset button, to keep it simple this will reset all examples. This is simply because when entering fullscreen mode, dragging/moving the image out of view, and pressing esc, the image will have 'vanished' (not in view anymore) so i thought id add a reset button
import { ref } from 'vue';
const componentKey = ref(0);

const forceRerender = () => {
  componentKey.value += 1;
};

forceRerender();

</script>

## Self Trained Upscaling Models

These examples feature my self trained upscaling models or interpolations I made.

> Example Controls: Left mouse button to drag the image or to move the slider, mouse wheel to zoom in, right mouse button to toggle left model on/off, releasing middle mouse button will activate a short flicker test for the left side of the slider. Do not work on mobile.

#### 2dcutout

A 2D Game Art Style example: Cutout art (256x256)

<div id="cutout">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/qVdCBgNA.png' :fileNamesList="cutoutfiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('cutout')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/>

  <summary>Full example (113 outputs)</summary>
  <p>

<div id="cutout_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/qVdCBgNA.png' :fileNamesList="cutoutfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('cutout_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/>

  </p>
