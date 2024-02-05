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
  import facefiles from './filelists/selftrained/face.json'
  import facefiles_selection from './filelists/selftrained/face_selection.json'
  import bendaydotsfiles from './filelists/selftrained/bendaydots.json'
  import bendaydotsfiles_selection from './filelists/selftrained/bendaydots_selection.json'
  import digitalartfiles from './filelists/selftrained/digitalart.json'

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
Most of these inputs are cropped into an interesting region and purposefully small (256x256). This should help not only with visual comparison but also faster loading times.

> Example Controls: Left mouse button to drag the image or to move the slider, mouse wheel to zoom in, right mouse button to toggle left model on/off, releasing middle mouse button will activate a short flicker test for the left side of the slider. Controls do not work on mobile. Model selection is filterable, so a model name can be typed in and it will filter for outputs containing that string.

### Filtered Results
> For this Section I visually went through all the outputs and feature a filtered selection of outputs here I personally found acceptable to save you time going through all the outputs.
You can still go to the Unfiltered Results Section, which contains all the outputs.

> (This Section is wip so examples are commented out)

<!---

<br/>

#### 2dcutout

A 2D Game Art Style example: Cutout art (256x256)

<div id="cutout_selection">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/qVdCBgNA.png' :fileNamesList="cutoutfiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('cutout_selection')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### face

A Face Photo example (cropped to interesting section, 256x256)

<div id="face_selection">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/UXgfK7yn.png' :fileNamesList="facefiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('face_selection')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/>


-->

### Unfiltered Results
This Section contains the full examples, meaning all outputs (113), from worst to acceptable to best, but Ill let you decide. This page, after all, is for you to get an impression on the outputs of models in comparison between each other.
<br/>



#### 2dcutout

A 2D Game Art Style example: Cutout art (256x256)

<div id="cutout_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/qVdCBgNA.png' :fileNamesList="cutoutfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('cutout_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### face

A Face Photo example (cropped to interesting section, 256x256)

<div id="face_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/UXgfK7yn.png' :fileNamesList="facefiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('face_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### bendaydots

A Bendaydot example (256x256)

<div id="bendaydots_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/MM6R3A2c.png' :fileNamesList="bendaydotsfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('bendaydots_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### digitalart

A digital art example (256x256)

<div id="digitalart_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/sXtLqRmX.png' :fileNamesList="digitalartfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('digitalart_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

<!---
Cannot use <details> as a collapsible html tag for unfiltered results directly under filtered results because it will not properly load the element, like

   <details>
  <summary>Unfiltered Outputs</summary>
  <div id="cutout_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/qVdCBgNA.png' :fileNamesList="cutoutfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('cutout_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
</details> 

-->
