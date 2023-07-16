<template>
  <div class="apartment" >
    <div><strong>Название:</strong> {{apartment.title}}</div>
    <div><strong>Описание:</strong> {{apartment.description}}</div>
  </div>
</template>

<script>
export default {
  name: "ApartmentItem",
  props: {
    apartment: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.apartment{
  display: grid;
  padding: 15px;
  border: 2px solid teal;
}
</style>