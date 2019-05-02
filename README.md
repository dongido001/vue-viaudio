# vue-viaudio

Dynamically/Reactively render videos and audios.

## Project setup

Install the package:

#### Using npm

```
    npm i @dongido/vue-viaudio
```

#### OR Using yarn

```
    yarn add @dongido/vue-viaudio
```

## Example Usage

```vue
<template>
  <div id="app">
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
import Media from '@dongido/vue-viaudio'

export default {
  name: 'app',
  components: {
    Media
  },
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

<style>
#app {
  width: 100%;
  text-align: center;
  margin-top: 40vh;
}
</style>

```

### Contribute

[GitHub]()
