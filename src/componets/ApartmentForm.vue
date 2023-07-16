<template>
  <div>
    <form @submit.prevent>
      <h3>Создания апартамента</h3>
      <input v-model="apartment.title" class="input" placeholder="Введите название" type="text">
      <input v-model="apartment.description" class="input" placeholder="Введите описание" type="text">
      <button @click="createApartment">Создать</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      apartment: {
        title: '',
        description: ''
      }
    }
  },
  methods: {

    createApartment() {
      this.apartment.id = Date.now()
      this.$emit('create', this.apartment)
      this.apartment = {
        title: '',
        description: ''
      }
    }
  }
}
</script>

<style>
.input {
  padding: 10px;
  border: 1px solid teal;
}
</style>