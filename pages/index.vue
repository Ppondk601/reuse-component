<template>
  <div class="container">
    <u-form v-bind="props">
      <template #header> PORAMINJA </template>
      <template v-slot:main="{ input }">
        <input type="text" v-model="input.value.userName" />
        <input type="email" v-model="input.value.userEmail" />
        <input type="text" v-model="input.value.userComment" />
      </template>
      <template #footer><button>เพิ่มสินค้า</button></template>
    </u-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      props: {
        target: 'http://localhost:6969/comments/',
        model() {
          return {
            userName: '',
            userEmail: '',
            userComment: '',
          }
        },
      },
    }
  },
}
</script>

<style lang="scss" scoped></style>
