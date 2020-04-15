
<!-- Added to test is if my "componants/slice" folder was the problem  -->
<template>
  <div>

    <br>
    <div><prismic-rich-text class="homepage-banner-box" :field="sliceRaw.primary.header1" /></div>
    <div><prismic-rich-text class="homepage-banner-box" :field="sliceRaw.primary.text1" /></div>
    <br><br>

    Multiple image views PICTURE TAG
    <br><br>

    <picture>
      <source media="(min-width: 769px)" :srcset="sliceRaw.primary.image1.desktop.ur">
      <source media="(min-width: 479px)" :srcset="sliceRaw.primary.image1.tablet.url">
      <img :src="sliceRaw.primary.image1.url" :alt="sliceRaw.primary.image1.alt">
    </picture>
    <br><br>

    Multiple image views PRISMIC-IMAGE TAG
    <br><br>

    <prismic-image class="homepage-banner-image" :field="sliceRaw.primary.image1" />
    <br><br>

    Singel view PRISMIC-IMAGE TAG
    <br><br>

    <prismic-image class="homepage-banner-image" :field="sliceRaw.primary.image_singel1" />
    <br><br>

  </div>
</template>

<script>
export default {
  props: ['sliceRaw'],
  name: 'slice-impact-image'
}
</script>


