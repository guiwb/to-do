<template>
  <ul>
    <li v-for="(item, index) in items" :key="item+index" :title="item">
      <span v-text="item" />
      <i class="material-icons" @click="$emit('removeItem', index)">delete</i>
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

<style lang="scss" scoped>
ul {
  display: flex;
  gap: 15px;
  width: 50%;
  flex-wrap: wrap;
  margin-top: 30px;
  justify-content: center;

  li {
    display: flex;
    align-items: center;
    padding: 8px 15px;
    background-color: $black-light;
    color: white;
    border-radius: 20px;
    font-size: 14px;
    transition: all 0.25s ease;
    max-width: 100%;

    &:hover {
      background-color: $purple;
      transform: translateY(-5px);
    }

    span {
      overflow: hidden;
      padding: 3px 0;
      text-overflow: ellipsis;
      white-space: nowrap;
    }

    i {
      font-size: 18px;
      margin-left: 10px;
      cursor: pointer;
    }
  }
}
</style>
