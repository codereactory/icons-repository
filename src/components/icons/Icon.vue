<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    version="1.1"
    :width="width"
    :height="height"
    :aria-labelledby="title"
    :viewBox="viewBox"
    :fill="color"
    :fill-opacity="opacity"
    :style="styleObject"
  >
    <title>{{ displayTitle }}</title>
    <g>
      <component :is="iconComponent" />
    </g>
  </svg>
</template>

<script>
// Application icons and a map to a string representation.
import IconHome from './IconHome.vue'
import IconProfile from './IconProfile.vue'
import IconCart from './IconCart.vue'

const iconsMap = {
  'home': IconHome,
  'profile': IconProfile,
  'cart': IconCart,
}

export default {
  name: 'icon-base',

  props: {
    // Controll property for what to render inside the
    // inner html
    variant: {
      type: String,
      required: true,
      
      // A nice validation message, when a developer 
      // tries to render a missing icon.
      validator(value) {
        const iconKeys = Object.keys(iconsMap)
        const exists = iconKeys.indexOf(value) !== -1
        if (!exists) {
          console.warn(`Missing icon variant: '${value}'. Must be one of`, iconKeys)
        }
        return exists
      },
    },
    title: {
      type: String,
      default: '',
    },
    width: {
      type: [Number, String],
      default: '100%',
    },
    height: {
      type: [Number, String],
      default: '100%',
    },
    color: {
      type: String,
      default: '#000',
    },
    opacity: {
      type: String,
      default: '1',
    },
    viewBox: {
      type: String,
      default: '0 0 100 100',
    },
  },

  data() {
    return {
      // some SVG specific attributes, ignore these
      styleObject: {
        'shape-rendering': 'geometricPrecision',
        'text-rendering': 'geometricPrecision',
        'image-rendering': 'optimizeQuality',
      },
    }
  },

  computed: {
    // dynamic component resolver, based on controlling property
    iconComponent() {
      return iconsMap[this.variant]
    },
    displayTitle() {
      return this.title || this.variant
    },
  },
}
</script>
