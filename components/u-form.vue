<template>
  <div class="u-form">
    <form @submit.prevent="addData">
      <header>
        <slot name="header">Header form</slot>
      </header>
      <main>
        <slot name="main" v-bind="{ input: inputData }"></slot>
      </main>
      <footer>
        <slot name="footer"></slot>
      </footer>
    </form>
    {{ this.inputData.value }}
  </div>
</template>

<script>
export default {
  props: {
    target: {
      type: String,
    },
    model: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      inputData: {
        value: this.model(),
      },
    }
  },
  methods: {
    addData() {
      try {
        const response = fetch(this.target, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            id: Math.floor(Math.random() * 100000),
            ...this.inputData.value,
          }),
        })
      } catch (error) {
        console.log(error)
      }
    },
  },
}
</script>

<style lang="scss" scoped></style>
