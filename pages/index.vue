<template>
  <section>
    <h1>To-Do App</h1>
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
