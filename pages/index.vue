<template>
  <section>
    <h1>ToDo App</h1>
    <InputField
      v-model="text"
      name="text"
      placeholder="Digite alguma coisa..."
      @keyup.enter.native="addItem"
      @blur="addItem" />
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
      if(!this.text) return

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
  display: flex;
  flex-direction: column;
  align-items: center;

  h1 {
    font-size: 50px;
    font-weight: 200;
    margin-bottom: 50px;
    transition: color 0.25s ease;

    &:hover {
      color: $purple;
    }
  }
}
</style>
