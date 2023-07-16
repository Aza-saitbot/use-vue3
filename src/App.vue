<template>
  <div class="app">
    <h1>Список апартаментов</h1>
    <div class="app__header">
      <my-button @click="showDialog">Создать апартамент</my-button>
      <my-select
          :options="sortOptions"
          v-model="selectedSort"
      />
    </div>
    <my-dialog v-model:show="visibleDialog">
      <apartment-form @create="createApartment"/>
    </my-dialog>
    <apartment-list
        :apartments="sortedApartments"
        @remove="removeApartment"
        v-if="!isApartmentsLoading"
    />
    <div v-else>...идет загрузка</div>
  </div>
</template>

<script>
import ApartmentList from './componets/ApartmentList.vue'
import ApartmentForm from './componets/ApartmentForm.vue'
import axios from 'axios'

export default {
  components: {
    ApartmentList,
    ApartmentForm
  },
  data() {
    return {
      apartments: [],
      visibleDialog: false,
      isApartmentsLoading: false,
      selectedSort: '',
      sortOptions: [
        {value: 'title', name: 'По названию'},
        {value: 'body', name: 'По содержанию'}
      ]
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
    },
    async fetchApartments() {
      try {
        this.isApartmentsLoading = true
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.apartments = response.data
      } catch (e) {
        alert('Ошибка при загрузке списка апартаментов!')
      } finally {
        this.isApartmentsLoading = false
      }
    }
  },
  mounted() {
    this.fetchApartments()
  },
  computed: {
    sortedApartments() {
      return [...this.apartments].sort((apart1, apart2) => {
        return apart1[this.selectedSort]?.localeCompare(apart2[this.selectedSort])
      })
    }
  }
  ,
  watch: {

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

.app__header {
  margin: 15px 0;
  display: flex;
  justify-content: space-between;
}

</style>