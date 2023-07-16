<template>
  <div>
    <h3>Список апартаментов</h3>
    <apartment-item :apartment="apartment" v-for="apartment in apartments" />
  </div>
</template>

<script>
import ApartmentItem from "./ApartmentItem.vue";
export default {
  components: {ApartmentItem},
  props: {
    apartments:{
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>