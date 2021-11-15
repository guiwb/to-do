<template>
  <section>
    <h1>ToDo App</h1>
    <InputField v-model="text" name="text" @keyup.enter.native="addItem" />
    <ToDoList :items="items" @removeItem="removeItemByIndex" />
  </section>
</template>

<script>
import InputField from '@/components/UI/InputField'
import ToDoList from '@/components/ToDoList'

export default {
  components: {
    InputField,
    ToDoList
  },
  data: () => ({
    items: [],
    text: ''
  }),
  methods: {
    addItem() {
      this.items.push(this.text)
      this.text = ''
    },
    removeItemByIndex(index) {
      this.items.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
section {
  margin-top: 50px;
  min-height: 100vh;
  text-align: center;

  h1 {
    font-size: 50px;
    font-weight: 200;
    margin-bottom: 50px;
  }
}
</style>
