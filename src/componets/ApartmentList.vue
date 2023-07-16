<template>
  <div v-if="apartments.length > 0">
    <h3>Список апартаментов</h3>
    <apartment-item
        :apartment="apartment"
        v-for="apartment in apartments"
        :key="apartment.id"
        @remove="$emit('remove',apartment)"
    />
  </div>
  <div v-else class="empty">
    <h3>Список пуст</h3>
  </div>
</template>

<script>
import ApartmentItem from "./ApartmentItem.vue"

export default {
  components: {ApartmentItem},
  props: {
    apartments: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.empty {

  text-align: center;
}
</style>