---
title: Selftrained
description: Visual Comparison of Multiple Self-Trained Models
layout: doc
outline: [2, 4]
---

<script setup lang="ts">
  import imageCompare from "vue-image-compare2";
  import ImageSlider from './components/imageslider.vue' // the vue image slider example comparison component
  import cutoutfiles from './filelists/selftrained/cutout.json'
  import cutoutfiles_selection from './filelists/selftrained/cutout_selection.json'
  import facefiles from './filelists/selftrained/face.json'
  import facefiles_selection from './filelists/selftrained/face_selection.json'
  import bendaydotsfiles from './filelists/selftrained/bendaydots.json'
  import bendaydotsfiles_selection from './filelists/selftrained/bendaydots_selection.json'
  import digitalartfiles from './filelists/selftrained/digitalart.json'
  import digitalartfiles_selection from './filelists/selftrained/digitalart_selection.json'
  import aniscreenfiles from './filelists/selftrained/aniscreen.json'
  import aniscreenfiles_selection from './filelists/selftrained/aniscreen_selection.json'
  import carfiles from './filelists/selftrained/car.json'
  import carfiles_selection from './filelists/selftrained/car_selection.json'

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

These examples feature my self trained upscaling models and can give an impression on which models might do well on what kind of input.   
Most of these inputs are cropped into an interesting region and purposefully small (256x256).    
  
This should help not only with visual comparison but also faster loading times.   

> Example Controls: Left mouse button to drag the image or to move the slider, mouse wheel to zoom in, right mouse button to toggle left model on/off, releasing middle mouse button will activate a short flicker test for the left side of the slider. Controls do not work on mobile. Model selection is filterable, so a model name can be typed in and it will filter for outputs containing that string.   

<br/><br/>

### Filtered Results
For this Section I visually went through all the outputs and feature a filtered selection of outputs here I personally found acceptable to save you time going through all the outputs.    
I also write which model/output I liked best for that specific input out of all of these. These will be the first in the drop down, the rest will be sorted alphabetically. I linked these models to their [openmodeldb](https://openmodeldb.info/) page if available, otherwise all these models can be found in my [google drive folder](https://drive.google.com/drive/folders/1coYgan0VDo578MVO1LUpjpsxdY3LMyJW?usp=drive_link).   
  
You can still go to the [Unfiltered Results Section](#unfiltered-results), which contains all the self-trained outputs.<br/><br/>    

#### car

A photo example (cropped to interesting section, 256x256).   

For this input we are looking for faithful, detail-preserving models that:    
- preserve depth of field - do not deblur blurry background, look for example at the tail lights of the car in the background.    
- preserve details - look for example at the WESTFALIA and the VOLKSWAGEN text and also texture and scratches on the car.   

For 4x my favorite output is 4xNomos8kHAT-L_bokeh_jpg.    
Honorable mentions are also [4xNomosUniDAT2_box](https://openmodeldb.info/models/4x-NomosUniDAT2-box) for a little bit sharper output that does not overdo it (but notice the 'volkswagen' text looses some consistency), [4xNomosUniDAT_bokeh_jpg](https://openmodeldb.info/models/4x-NomosUniDAT-bokeh-jpg) and 4xNomosUniHAT-L_bokeh_jpg.     

For 2x my favorite output is 2xNomosUni_dat2_multijpg   
Honorable mentions (and more lightweight alternatives are): 2xNomosUni_esrgan_multijpg, 2xNomosUni_compact_multijpg_ldl and [2xNomosUni_span_multijpg](https://openmodeldb.info/models/2x-NomosUni-span-multijpg).     

<div id="car_selection">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/tk7iBXnn.png' :fileNamesList="carfiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('car_selection')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### face

A Face Photo example (cropped to interesting section, 256x256)

For 4x, I recommend checking out the [4xFaceUpSharpDAT](https://openmodeldb.info/models/4x-FaceUpSharpDAT) model output - this model has a tendency to over-interpret everything as hair, this is why it does well on this input.   
A safter alternative is [4xFaceUpDAT](https://openmodeldb.info/models/4x-FaceUpDAT).   
Both of these models are trained on a [self-curated dataset (FaceUp)](https://www.youtube.com/watch?v=TBiVIzQkptI) which I made out of the FFHQ dataset.      
Other 4x models that do well here and are not specialized/ trained on faces alone are [4xNomos8kSCHAT-L](https://openmodeldb.info/models/4x-Nomos8kSCHAT-L), [4xNomos8kSCHAT-S](https://openmodeldb.info/models/4x-Nomos8kSCHAT-S) and [4xNomos8kSCSRFormer](https://openmodeldb.info/models/4x-Nomos8kSCSRFormer).   

For 2x, I recommend checking out the 2xNomosUni_dat_multijpg model output. One could also go with the lightweight alternatives 2xNomosUni_compact_multijpg_ldl or 2xNomosUni_span_multijpg_ldl with this input.   

<div id="face_selection">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/UXgfK7yn.png' :fileNamesList="facefiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('face_selection')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### digitalart

A digital art example (cropped to interesting section, 256x256).   

For 4x, I recommend checking out the [4xNomosUniDAT2_box](https://openmodeldb.info/models/4x-NomosUniDAT2-box) model output.  
And for a softer touch, the [4xLSDIRDAT](https://openmodeldb.info/models/4x-LSDIRDAT) model output (or one of my newest, 4xNomosUni_rgt_multijpg).    

For 2x, I recommend checking out the 2xNomosUni_dat_multijpg output.  

<div id="digitalart_selection">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/sXtLqRmX.png' :fileNamesList="digitalartfiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('digitalart_selection')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### aniscreen

A anime frame example (cropped to interesting section, 256x256)   

While some of my models like the '_multijpg' models are made to preserve depth of field, for this specific input we may want models that deblur. Also details preserving, by looking at those wooden floor boards (wood texture lines present?) so:   

For 4x i liked the [4xHFA2k](https://openmodeldb.info/models/4x-HFA2k) output most, which deblurs but preserves details well. Second [4xNomos8kSCHAT-L](https://openmodeldb.info/models/4x-Nomos8kSCHAT-L)   

For 2x it would be [2xHFA2kCompact](https://openmodeldb.info/models/2x-HFA2kCompact). Second 2xHFA2kSwinIR-S.   

<div id="aniscreen_selection">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/rAcoxotm.png' :fileNamesList="aniscreenfiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('aniscreen_selection')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### 2dcutout

A 2D Game Art Style example: Cutout art (cropped to interesting section, 256x256)   

What we can look out for here is for example how well the lines on the red shirt of that guy to the right are preserved / still visible on the output.   
Or the lines on the light/cut part of that right wooden stake on the left side.   

4x models that did fairly well are 4xNomosUniDAT2_box, 4xNomos8kHAT-L_bokeh_jpg, 4xNomosUniDAT_bokeh_jpg and 4xNomosUni_dat2_multijpg.   

2x model that did well is 2xNomosUni_dat2_multijpg.   


<div id="cutout_selection">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/qVdCBgNA.png' :fileNamesList="cutoutfiles_selection"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('cutout_selection')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>



### Unfiltered Results
This Section contains the full examples, meaning all outputs (113). This page, after all, is for you to get an impression on the outputs of models in comparison between each other.
<br/>

#### car

A photo example (cropped to interesting section, 256x256)

<div id="car_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/tk7iBXnn.png' :fileNamesList="carfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('car_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
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

#### digitalart

A digital art example (cropped to interesting section, 256x256)

<div id="digitalart_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/sXtLqRmX.png' :fileNamesList="digitalartfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('digitalart_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### aniscreen

A anime frame example (cropped to interesting section, 256x256)

<div id="aniscreen_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/rAcoxotm.png' :fileNamesList="aniscreenfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('aniscreen_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### 2dcutout

A 2D Game Art Style example: Cutout art (cropped to interesting section, 256x256)

<div id="cutout_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/qVdCBgNA.png' :fileNamesList="cutoutfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('cutout_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
<button v-if="fullscreenEnabled" @click="forceRerender()" style="color:mediumseagreen;"><strong>Reset examples</strong></button>  
<br/><br/><br/>

#### bendaydots

A Bendaydot example (cropped to interesting section, 256x256)

<div id="bendaydots_full">
<ImageSlider :key="componentKey" inputImageURL='https://i.slow.pics/MM6R3A2c.png' :fileNamesList="bendaydotsfiles"/>
</div>
<button v-if="fullscreenEnabled" @click="enterFullscreen('bendaydots_full')" style="color:mediumseagreen;"><strong>FULLSCREEN (Exit with ESC)</strong></button><br/>
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
