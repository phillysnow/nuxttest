
<template>
  <div class="container">
    <div>

      <h1 class="title">
        pages/test/_uid.vue
      </h1>
      <br><br>

      <section class="text">
        <prismic-rich-text class="homepage-banner-box" :field="testuid.data.header" />
      </section>
      <br><br>

      <section class="text">
        <prismic-rich-text class="homepage-banner-box" :field="testuid.data.text" />
        <br><br>
      </section>

      <section class="images">

        Multiple image views PICTURE TAG
        <br><br>

        <picture>
          <source media="(min-width: 769px)" :srcset="testuid.data.image.desktop.ur">
          <source media="(min-width: 479px)" :srcset="testuid.data.image.tablet.url">
          <img :src="testuid.data.image.url" :alt="testuid.data.image.alt">
        </picture>
        <br><br>

        Multiple image views PRISMIC-IMAGE TAG
        <br><br>

        <prismic-image class="homepage-banner-image" :field="testuid.data.image" />
        <br><br>

        Singel view PRISMIC-IMAGE TAG
        <br><br>

        <prismic-image class="homepage-banner-image" :field="testuid.data.image_singel" />
        <br><br>

      </section>

      <h2>As slice [page inlined]</h2>

      <!-- SLICES loop inlined -->
      <div v-for="(slice, index) in slices" :key="'slice-' + index">
        <!-- IMAGE -->
        <template v-if="slice.slice_type === 'image'">
          <slice-image :sliceRaw="slice"/>
        </template>
      </div>

      <br><br>
      <h2>As slice [components/slices.vue]</h2>

      <!-- SLICES loop as component -->
      <site-slices :slicesRaw="slices"/>

    </div>

  </div>

</template>

<script>

import siteSlices   from '~/components/slices.vue'
import sliceImage  from '~/components/slices/image.vue'

export default {
  components: {
    siteSlices,
    sliceImage
  },
  async asyncData ({ params, $prismic }) {
    const testuid = await $prismic.api.getByUID('test', params.uid)
    const slices = testuid.data.body
    return { testuid, slices}
  }
}

</script>

<style>

img {
  width: 320px;
  height: auto;
}

.container {
  margin: 40px auto;
  min-height: 100vh;
  width: 80%;
  min-width: 300px;
  text-align: center;

}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 40px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 24px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
