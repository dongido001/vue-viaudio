<template>
  <div class="example">
    <Media 
      :kind="'video'"
      :isMuted="(false)"
      :src="['https://www.w3schools.com/html/mov_bbb.mp4']"
      :poster="'https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217'"
      :autoplay="true"
      :controls="true"
      :loop="true"
      @pause="handle()"
      :ref="'fish'"
      :style="{width: '500px'}"
    >
    </Media>
  </div>
</template>

<script>
import Media from './vue-viaudio'
import { setTimeout } from 'timers';

export default {
  components: {
   Media
  },
  name: 'Example',
  methods: {
    handle() {
      console.log('Video paused!, playing in 2 sec...')

      setTimeout( () => {
        this.$refs.fish.play() 
      }, 2000)
    }
  }
}
</script>
