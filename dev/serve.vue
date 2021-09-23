<script lang="ts">
import { defineComponent } from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
// import { WaveFormsSample } from '@/entry.esm';

export default defineComponent({
  name: 'ServeDev',
  // components: {
  //  WaveFormsSample,
  // }
});
</script>

<template>
  <div id="app">
    <wave-forms-sample />
  </div>
</template>
