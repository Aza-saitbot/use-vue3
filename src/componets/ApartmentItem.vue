<template>
  <div class="apartment">
    <div>
      <div><strong>Название:</strong> {{ apartment.title }}</div>
      <div><strong>Описание:</strong> {{ apartment.body }}</div>
    </div>
    <my-button style="align-self: flex-end" @click="$emit('remove',apartment)">удалить</my-button>
  </div>
</template>

<script>

export default {

  props: {
    apartment: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.apartment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  border: 2px solid teal;
}
</style>