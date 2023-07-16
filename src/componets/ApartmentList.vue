<template>
  <div v-if="apartments.length > 0">
    <h3>Список апартаментов</h3>
    <TransitionGroup name="apartment-list" tag="ul">
      <apartment-item
          :apartment="apartment"
          v-for="apartment in apartments"
          :key="apartment.id"
          @remove="$emit('remove',apartment)"
      />
    </TransitionGroup>

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
.apartment-list-move,
.apartment-list-enter-active,
.apartment-list-leave-active {
  transition: all 0.4s ease;
}
.apartment-list-enter-from,
.apartment-list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}


</style>