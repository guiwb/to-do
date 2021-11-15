<template>
  <div>
    <label v-if="label" :for="name" v-text="label" />
    <input :id="name" v-bind="$attrs" v-model="model" type="text">
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: false,
      default: ''
    },
    name: {
      type: String,
      required: true
    },
    value: {
      type: String,
      required: false,
      default: ''
    }
  },
  computed: {
    model: {
      get() {
        return this.value
      },
      set(value) {
        this.$emit('input', value)
      }
    }
  }
}
</script>
