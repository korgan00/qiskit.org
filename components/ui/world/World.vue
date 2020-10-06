<template>
  <div class="events-world">
    <canvas class="events-world__canvas" width="640" height="480" />
    <div id="LocationData" class="events-world__location-data hidden">
      <span>Location name</span>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        In rutrum tellus eget lacus blandit sodales.
        Maecenas vitae eleifend felis, vel ultrices mi.
        Nulla tincidunt sagittis commodo.
      </p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Component } from 'vue-property-decorator'
import { EventsWorldRenderer } from './src/EventsWorld'

@Component
export default class extends Vue {
  mounted () {
    const canvas: HTMLCanvasElement | null = this.$el.querySelector('.events-world__canvas')

    if (canvas) {
      const eventsWorld: EventsWorldRenderer = new EventsWorldRenderer(canvas, () => {})
      eventsWorld.Run()
    }
  }
}
</script>

<style lang="scss" scoped>
.events-world {
  top: 100px;
  left: 100px;
  width: 640px;
  display: block;
  position: relative;

  &__location-data {
    display: block;
    position: absolute;
    font-size: 1em;
    width: 200px;
    top: 100px;
    right: 20px;
    background-color: white;
    border: 3px solid #be95ff;
    color: #393939;
    border-radius: 5px;
    padding: 15px 10px;
    &.hidden {
      display: none;
    }
    span {
      font-size: 1.2em;
      font-weight: bold;
    }
    p {
      font-size: 1em;
      padding-top: 0.5em;
    }
  }
}
</style>
