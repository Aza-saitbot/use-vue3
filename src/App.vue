<template>
  <div>
    <apartment-form @create="createApartment" />
    <apartment-list :apartments="apartments"/>
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
        { id: 1,title:'Квартира 1+1',description: 'ОРЕ 1'},
        { id: 2,title:'Квартира 1+2',description: 'ОРЕ 2'},
        { id: 3,title:'Квартира 1+3',description: 'ОРЕ 3'},
        { id: 4,title:'Квартира 1+4',description: 'ОРЕ 4'},
      ],
    }
  },
  methods: {

    createApartment(apartment) {
      console.log('apartment',apartment)
      this.apartments.push(apartment)
    }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}


</style>