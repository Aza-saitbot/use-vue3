<template>
  <input :value="modelValue" @input="updateValue" class="input" type="text">
</template>

<script>
export default {
  name: "MyInput",
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateValue(event) {
      this.$emit("update:modelValue", event.target.value);
    }
  }
}
</script>

<style scoped>
.input {
  padding: 10px;
  border: 1px solid teal;
}
</style>