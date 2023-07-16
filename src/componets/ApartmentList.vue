<template>
  <div>
    <h3>Список апартаментов</h3>
    <div class="apartment" v-for="apartment in apartments">
      <div><strong>Название:</strong> {{apartment.title}}</div>
      <div><strong>Описание:</strong> {{apartment.description}}</div>
    </div>
  </div>
</template>

<script>
export default {
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