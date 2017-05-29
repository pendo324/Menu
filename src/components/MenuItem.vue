<template>
  <div class="menuitem" v-bind:class="{ 'selected': selectedItem }">
    <slot>
    </slot>
  </div>
</template>

<script>
export default {
  name: 'menu-item',
  props: ['selectedItem']
};
</script>

<style>
.selected {
  border-color: red;
  border: solid 0.3em;
}
</style>
