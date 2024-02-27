<template>
    <div>
      <el-select v-model="after" filterable placeholder="Select Model" class="left" :teleported=falseBoolean
        :automatic-dropdown=trueBoolean placement="bottom-start">
        <el-option v-for="item in options" :key="item.value" :label="item.text" :value="item.value" />
      </el-select>
      <el-select v-model="before" filterable placeholder="Select Model" class="right"
        :teleported=falseBoolean :automatic-dropdown=trueBoolean placement="bottom-end">
        <el-option v-for="item in options" :key="item.value" :label="item.text" :value="item.value" />
      </el-select>
    </div>
  
    <image-compare :before="before" :after="after" isZoomable isDraggable :key="componentKey" :zoom="zoom"
      @wheel.prevent @touchmove.prevent @scroll.prevent />
  </template>
  
  <script setup lang="ts">
  import { ref, watch } from "vue";
  import imageCompare from "vue-image-compare2";
  
  const falseBoolean:Boolean = false;
  const trueBoolean:Boolean = true;
  
  // the props
  const props = defineProps({
    inputImageURL: String,
    fileNamesList: {
      type: Array,
      default: () => []
    }
  });
  
  // the selection options
  let options = ref();
  // the very first examples loaded to show a fast result before in the background the selector has been build by fetching the github folder sources
  const after = ref(); // left
  const before = ref(); // right
  // the defined key on the component so it will tigger a rerender if we change this value
  const componentKey = ref(0);
  // the watchers, which detect selection change and trigger a force rerender on the image comparison slider component
  watch(after, () => {
    forceRerender();
  });
  watch(before, () => {
    forceRerender();
  });
  // we force the image comparison slider component rerender because otherwise it will build only on page load and you can never change images to compare
  function forceRerender() {
    componentKey.value += 1;
  }
  // set zoom options (doesnt make sense to zoom too deep since it will be pixelated just because of image size)
  const zoom = { min: 1, max: 4 };


  let publicUrls = props.fileNamesList ? props.fileNamesList.map((file: any) => file.public_url) : [];
  let modelNames = props.fileNamesList ? props.fileNamesList.map((file: any) => file.model_name) : [];

  console.log("component")
  console.log(publicUrls)
  console.log(modelNames)
  
  options.value = []; // empty options array
  options.value.push({ text: "Input", value: props.inputImageURL }); // push first image as input which is not in the upscale folder but the inputs folder
  // build the options array with the data
  for (let i = 0; i < publicUrls.length; i++) {
    let text = modelNames[i];
    let value = publicUrls[i];
    let object = { text: text, value: value };
    options.value.push(object);
  }

  console.log("options")
  console.log(options)
  
  // set image slider comparison images, also this will trigger a component refresh since we have set the forceRenderer on value change
  after.value = options.value[0].value;
  before.value = options.value[1].value;
  </script>
  
  <style>
  .before-name {
    color: black;
  }
  
  .after-name {
    color: black;
  }
  
  .right {
    position: absolute;
    right: 0px;
    text-align: center;
    width: 50%;
  }
  
  .left {
    text-align: center;
    width: 50%;
  }
  </style>