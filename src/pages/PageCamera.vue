<template>
  <q-page class="constrain-more q-pa-md">
    
        <div class="text-center q-pa-md">
    <q-btn unelevated rounded color="primary" label="Guardar Foto" />
    </div>

    <div class="camera-frame q-pa-md">
          <video
            v-show="!imageCaptured"
            ref="video"
            class= "full-width"
            autoplay
          />

          <canvas
            v-show="imageCaptured"
            ref="canvas"
            class="full-width"
            height="240"
          />

    </div>
    <div class="text-center q-pa-md">
      <q-btn
      @click="captureImage"
      padding="xl"
      color="primary"
      round
      icon="eco"
      label="Tomar Foto"
    />
      <q-btn
      @click="captureVid"
      padding="xl"
      color="primary"
      round
      icon=""
      label="Grabar video"
    />
    </div>

  </q-page>
</template>

<script>

import {uid} from 'quasar'
require('md-gum-polyfill')

export default {
  name: 'PageCamera',
  data(){
  return{
    imageCaptured:false,
    videoCaptured:false
    }
  },
  methods:{
    initCamera(){
      navigator.mediaDevices.getUserMedia({
        video: true
      }).then(stream=>{
        this.$refs.video.srcObject = stream
      })
    },
  captureImage(){
    let video=this.$refs.video
    let canvas=this.$refs.canvas
    canvas.width= video.getBoundingClientRect().width
    canvas.height= video.getBoundingClientRect().height
    let context = canvas.getContext('2d')
    context.drawImage(video, 0, 0, canvas.width, canvas.height)
    this.imageCaptured=true
  },
    captureVid(){
    let video=this.$refs.video
    let canvas=this.$refs.canvas
    canvas.width= video.getBoundingClientRect().width
    canvas.height= video.getBoundingClientRect().height
    let context = canvas.getContext('2d')
    context.drawImage(video, 0, 0, canvas.width, canvas.height)
    this.videoCaptured=true
  }
  },
  mounted(){
    this.initCamera()
  }
}

</script>

<style lang="sass">
  .camera-frame
    border: 2px solid $grey-10
    border-radius: 8px
</style>