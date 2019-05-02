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

#### Demos

- [Basic usage demo](https://codesandbox.io/s/m5o1vl2pm9)
- [Reactive example](https://codesandbox.io/s/m4601xq0zp)

## Example Usage

### Basic usage - Play a video

```javascript
<script>
import Media from '@dongido/vue-viaudio'

export default {
  name: 'app',
  components: {
    Media
  },
}
</script>

<template>
  <div id="app">
    <Media 
      :kind="'video'"
      :controls="true"
      :src="['https://www.w3schools.com/html/mov_bbb.mp4']"
    >
    </Media>
  </div>
</template>
```

### Basic usage - Play an audio

```javascript
<script>
import Media from '@dongido/vue-viaudio'

export default {
  name: 'app',
  components: {
    Media
  },
}
</script>

<template>
  <div id="app">
    <Media 
      :kind="'audio'"
      :controls="true"
      :src="['https://www.w3schools.com/html/mov_bbb.mp4']"
    >
    </Media>
  </div>
</template>
```

A bit advanced usage - with events
```javascript
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
      :ref="'fish'"
      :style="{width: '500px'}"
      @pause="handle()"
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

## Media sources

This package can accept its source of media from either the `:src` or [`:srcObject`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/srcObject) property. 

The `src` property can be either a string or an array. 

The `:srcObject` is particularly useful when you need to render a stream source like from WebRTC.

## Properties  - supports all Video and Audio Element properties.

| Props                    | Required                                | Description                     | 
| ------------------------ | --------------------------------------- | -------------------------       |
| `src`  [Array or String ] | *True* (if `srcObject` is not provided) | The source of the media         |
| `srcObject` [Object]     | *True* (if `src` is not provided)       | The source of the media         |
| `kind` [String]          | *True*                                  | It's either `audio` or `video`. |

It accepts all [video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Attributes) and [audio](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio#Attributes) attributes. You just need to pass the one you need. You can also bind them if you need some reactivity.

## Video Events

You can listen to video element events when they happen. These events are available when you pass the prop `kind` as `video`.

| Events                   | Description                     | 
| ---------------- | -------------------------       |
| `canplay`        | The browser can play the media |
| `canplaythrough` | The browser estimates it can play the media up to its end without stopping for content buffering.|
| `complete`       | The rendering of an OfflineAudioContext is terminated.|
| `durationchange` | The duration attribute has been updated.|
| `emptied`        | The media has become empty|
| `ended`          | Playback has stopped because the end of the media was reached.|
| `loadeddata`     | The first frame of the media has finished loading.|
| `pause`          | Playback has been paused.|
| `play`           | Playback has begun.|
| `loadedmetadata` | The metadata has been loaded.|
| `playing`        | Playback is ready to start after having been paused or delayed due to lack of data.|
| `ratechange`     | The playback rate has changed.|
| `seeked`         | A seek operation completed.
| `seeking`        | A seek operation began.|
| `stalled`        | The user agent is trying to fetch media data, but data is unexpectedly not forthcoming.|
| `suspend`        | 	Media data loading has been suspended. |
| `timeupdate`     | The time indicated by the currentTime attribute has been updated.|
| `volumechange`   | Trggers when volume has changed.|
| `waiting`        | Triggers when the media has stoped playing because of temproray lack of data|

You can read more about these [events here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Attributes).

#### Example usage
Assuming, you want to listen to when the user pauses a video. You can do that using:

```javascript
<script>
import Media from '@dongido/vue-viaudio'

export default {
  name: 'app',
  components: {
    Media
  },
  methods: {
    handlePauseEvent() {
      console.log('The video is now paused.')
    }
  }
}
</script>

<template>
  <div id="app">
    <Media 
      :kind="'video'"
      :controls="true"
      :src="'https://www.w3schools.com/html/mov_bbb.mp4'"
      @pause="handlePauseEvent()" // The event
    >
    </Media>
  </div>
</template>
```

## Audio Events

You can also listen to audio element events when they happen. These events are available when you pass the prop `kind` as `audio`. You can listen to it same way as the video events.

You can read about these events [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio#Events).

### Contribute

[GitHub](https://github.com/dongido001/vue-viaudio)
