<template>
  <div>
    <form @submit.prevent>
      <h3>Создания апартамента</h3>
      <my-input v-model="apartment.title"  placeholder="Введите название" />
      <my-input v-model="apartment.description"  placeholder="Введите описание" />
      <my-button @click="createApartment">Создать</my-button>
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

</style>