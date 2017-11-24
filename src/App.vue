<template>
  <div id="app">
    <div class="video-preview">
       <img  v-for="(image, index) in images"
            v-lazy="image.thumb" 
            style="height: 100px" 
            @click="openGallery(index)">
    </div>
     <lightbox 
        :images="images" 
        ref="lightbox"
        :show-caption="false"
      ></lightbox>
  </div>
</template>

<script>

let images = [
  {
    thumb: 'https://i.imgur.com/wBJ0Uii.png',
    src: '..//videos/video.mp4',
    caption: '<h4>Hello World 1</h4>',
  },
  {
    thumb: 'https://i.imgur.com/wBJ0Uii.png',
    src: '..//videos/video.mp4',
    caption: '<h4>Hello World 2</h4>',
  }
]

import Lightbox from 'components/Lightbox'

import siteLoading from './siteloading.gif'

export default {
  components: {
    Lightbox,
  },

  data () {
    return {
      images,
      siteLoading,
    }
  },

  methods: {
    openGallery(index) {
      this.$refs.lightbox.showImage(index)
    }
  }
}
</script>
<style>
  .video-preview {
  margin: 5vw;
  padding-top: 10px;
  padding-bottom: 10px;
  display: flex;
  flex-flow: row wrap;
  max-width: 90vw;
  justify-content: flex-start;
  }
.video-preview img {
  margin: 10px;
}
</style>
