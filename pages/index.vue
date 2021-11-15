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

    <footer>
      <span v-if="loading">Atualizando...</span>
      <span v-else-if="updatedAt" @click="getUpdatedAt">
        Projeto atualizado em <strong>{{ updatedAt | formatDate }}</strong>
      </span>
    </footer>
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
  filters: {
    formatDate(value) {
      return new Date(value).toLocaleString('pt-BR')
    }
  },
  data: () => ({
    items: [],
    text: '',
    updatedAt: null,
    loading: true,
  }),
  mounted(){
    this.getUpdatedAt()
  },
  methods: {
    addItem() {
      if(!this.text) return

      this.items.push(this.text)
      this.text = ''
    },
    removeItemByIndex(index) {
      this.items.splice(index, 1)
    },
    async getUpdatedAt() {
      try {
        this.loading = true
        const response = await this.$axios('https://api.github.com/repos/guiwb/to-do')
        this.updatedAt = response.data.updated_at
      } catch (error) {
        this.$toast.error(error)
      } finally {
        this.loading = false
      }
    }
  }
}
</script>

<style lang="scss" scoped>
section {
  margin-top: 50px;
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

  footer {
    font-style: italic;
  }
}
</style>
