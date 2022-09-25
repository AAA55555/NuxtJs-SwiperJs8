# Swiperjs8-Nuxt

Nuxt2 project with tailwindcss v3, postcss v8, prettier v2, eslint v8, stylelint v14 and swiperjs v8.

## Example How to make Swiper JS 8 work with Nuxt Js 2
Just add `build.standalone: true` in `nuxt.config.js` and use the simiale code as written in [NuxtJs-SwiperJs7](https://github.com/seosmmbusiness/NuxtJs-SwiperJs7) and [NuxtJs-SwiperJs](https://github.com/seosmmbusiness/NuxtJs-SwiperJs) to make it work.
Additional you need to add `externals` to your webpack config.

Currently tested with "swiper": "^8.1.4"

Project also uses:
    "nuxt": "^2.15.7",
    "@nuxtjs/tailwindcss": "^5.0.3",
    "postcss": "^8.3.5",
    "prettier": "^2.3.2",
    "stylelint": "^14.8.0",
    "eslint": "^8.14.0",

On 29.04.2022 it has no deps needed to update.

The project contains some unused dependencies for testing purposes. In a real project, you may have many more dependencies and there may be some bugs.

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```
Второй вариант подключаения:

nuxt.config.js: 
```
plugins: [
    { src: '~/plugins/swiper-slider.js', mode: 'client' },
  ],
```

plugins/<swiper-slider.js>
```
import Swiper from 'swiper/core/core.js'

import Autoplay from 'swiper/modules/autoplay/autoplay.js'
import Pagination from 'swiper/modules/pagination/pagination.js'
import Thumbs from 'swiper/modules/thumbs/thumbs.js'
import Vue from 'vue'

const swiper = {
  install(Vue, options) {
    Vue.prototype.$swiper = Swiper
    Vue.prototype.$swiperModules = {
      Autoplay,
      Thumbs,
      Pagination,
    }
  },
}

Vue.use(swiper)
```

template-component
```
<template>
  <div>
    <div class="swiper my-swiper">
      <ul class="swiper-wrapper">
        <li v-for="i in 5" :key="i" class="swiper-slide">{{ i }}</li>
      </ul>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import 'swiper/swiper-bundle.min.css'

export default {
  name: 'AppTtt',
  mounted() {
    /* eslint-disable no-unused-vars */
    const swiper = new this.$swiper(`.my-swiper`, {
      modules: [this.$swiperModules.Pagination],
      pagination: {
        el: '.swiper-pagination',
        type: 'bullets',
        clickable: true,
      },
    })
  },
}
</script>
```
