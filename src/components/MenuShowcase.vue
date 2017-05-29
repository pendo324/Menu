<template>
  <div id="showcaseitem">
    <!--<transition name="fade" mode="out-in">-->
      <div v-if="selectedItem">
        <slot>
        </slot>
      </div>
    <!--</transition>-->
  </div>
</template>

<script>
export default {
  props: ['selectedItem'],
  mounted: function () {
    console.log(this.selectedItem);
  }
};
</script>

<style>

</style>
