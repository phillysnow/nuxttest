<template>
  <div class="container">
    <div>

      <h1 class="title">
        at-bug-prismic-nuxt--preview
      </h1>
      <br><br>

      <section class="text">
        <prismic-rich-text class="homepage-banner-box" :field="start.data.text" />
        <br><br>
      </section>

      <section class="images">

        Multiple image views
        <br><br>

        <picture>
          <source media="(min-width: 769px)" :srcset="start.data.image.desktop.ur">
          <source media="(min-width: 479px)" :srcset="start.data.image.tablet.url">
          <img :src="start.data.image.url" :alt="start.data.image.alt">
        </picture>
        <br><br>

        Singel view
        <br><br>

        <prismic-image class="homepage-banner-image" :field="start.data.image_singel" />

      </section>

    </div>

  </div>

</template>

<script>

export default {
  async asyncData ({ $prismic }) {
    const start = await $prismic.api.getSingle('startpage')
    return { start }
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
