---
title: Selftrained
description: Visual Comparison of Multiple Models
layout: doc
outline: [2, 4]
---

<script setup lang="ts">
  import imageCompare from "vue-image-compare2";
//import ImageSlider from './imageslider.vue' // the vue image slider example comparison component

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

let before = "https://drive.usercontent.google.com/download?id=1cse7S2Uws8T8RNbbjWoznXig4ZN2FoBs"
let after= "https://drive.usercontent.google.com/download?id=1cse7S2Uws8T8RNbbjWoznXig4ZN2FoBs"

let before1 = "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.3l2nfzcHhMemSZooiH3B3AHaFj%26pid%3DApi&f=1&ipt=f2a03722e2521a9b47426359ed6e0b9ef5915a050503cd22b43184a0d97a536f&ipo=images"
let after1 = "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.3l2nfzcHhMemSZooiH3B3AHaFj%26pid%3DApi&f=1&ipt=f2a03722e2521a9b47426359ed6e0b9ef5915a050503cd22b43184a0d97a536f&ipo=images"

</script>


## Examples

These examples feature 300+ model ouputs and display all of my generated output from the respective github folder. Bear in mind that some of these models serve a different purpose than upscaling, like for example some 1x denoising models. You find the links to the input image and all the generated outputs in the 'Details' Section beneath each example, in case you wanted to do your own upscaling comparison.

> Example Controls: Left mouse button to drag the image or to move the slider, mouse wheel to zoom in, right mouse button to toggle left model on/off, releasing middle mouse button will activate a short flicker test for the left side of the slider. Do not work on mobile.

### Photo

<br/>

<image-compare :before="before" :after="after"/>

<image-compare :before="before1" :after="after1"/>

#### Buddy

<div id="firstExample">
<ImageSliderGithub :key="componentKey" inputImageURL='https://drive.google.com/file/d/1cse7S2Uws8T8RNbbjWoznXig4ZN2FoBs/view?usp=drive_link' relativePathOutputFolder='output/lossless/photos/buddy' />
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('firstExample')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/>

<details>
  <summary>Details</summary>
  <p>

Input Image: 480x320 pixels

Input Image: [Image](https://drive.google.com/file/d/1cse7S2Uws8T8RNbbjWoznXig4ZN2FoBs/view?usp=drive_link)

Output Images: [Github Folder](https://github.com/Phhofm/upscale/tree/main/sources/output/lossless/photos/buddy)

  </p>
</details>