<template>
  <div>
    <div v-for="(slice, index) in slicesRaw" :key="'slice-' + index">

      <!-- IMAGE -->
      <template v-if="slice.slice_type === 'image'">
        <slice-image :sliceRaw="slice"/>
      </template>

    </div>
  </div>

</template>

<script>
import sliceImage  from '~/components/slices/image.vue'

export default {
  name: 'site-slices',
  props: [
    'slicesRaw'
  ],
  components: {
    sliceImage
  }
};
</script>

