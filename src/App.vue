<template>
  <div class="app">
    <h1>Список апартаментов</h1>
    <my-button style="margin: 15px 0" @click="showDialog">Создать апартамент</my-button>
    <my-dialog v-model:show="visibleDialog">
      <apartment-form @create="createApartment"/>
    </my-dialog>
    <apartment-list
        :apartments="apartments"
        @remove="removeApartment"
    />
  </div>
</template>

<script>
import ApartmentList from './componets/ApartmentList.vue'
import ApartmentForm from './componets/ApartmentForm.vue'

export default {
  components: {
    ApartmentList,
    ApartmentForm
  },
  data() {
    return {
      apartments: [
        {id: 1, title: 'Квартира 1+1', description: 'ОРЕ 1'},
        {id: 2, title: 'Квартира 1+2', description: 'ОРЕ 2'},
        {id: 3, title: 'Квартира 1+3', description: 'ОРЕ 3'},
        {id: 4, title: 'Квартира 1+4', description: 'ОРЕ 4'},
      ],
      visibleDialog: false
    }
  },
  methods: {
    createApartment(apartment) {
      this.apartments.push(apartment)
      this.visibleDialog = false
    },
    removeApartment(apartment) {
      this.apartments = this.apartments.filter(item => item.id !== apartment.id)
    },
    showDialog() {
      this.visibleDialog = true
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

</style>