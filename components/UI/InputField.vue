<template>
  <div class="input-group">
    <label v-if="label" :for="name" v-text="label" />
    <input :id="name" v-bind="$attrs" v-model="model" type="text" autocomplete="off" @blur="$emit('blur')">
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

<style lang="scss" scoped>
.input-group {
  display: flex;
  flex-direction: column;

  label {
    margin-bottom: 5px;
  }

  input {
    background-color: $black-dark;
    padding: 20px;
    border-radius: 50px;
    color: white;
    min-width: 300px;
    text-align: center;
    font-size: 20px;
    transition: background 0.25s ease;

    &::placeholder {
      color: $black-light;
    }

    &:focus {
      background-color: darken($black-dark, 2);
    }
  }
}
</style>
