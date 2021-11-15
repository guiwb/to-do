<template>
  <ul>
    <li v-for="(item, index) in items" :key="item+index">
      <span v-text="item" />
      <i class="material-icons" @click="$emit('removeItem', index)">close</i>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true
    }
  }
}
</script>

