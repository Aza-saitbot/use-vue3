<template>
  <div>
    <form @submit.prevent>
      <h3>Создания апартамента</h3>
      <div class="form">
        <my-input v-model="apartment.title"  placeholder="Введите название" />
        <my-input v-model="apartment.description"  placeholder="Введите описание" />
      </div>
      <my-button @click="createApartment" style="margin: 10px 0" >Создать</my-button>
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
.form{
  display: flex;
  gap: 10px;
  padding: 10px 0;
}
</style>