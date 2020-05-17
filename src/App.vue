<template>
  <div>
    {{ name }}
  </div>
</template>

<script>
  export default {
    mounted() {
      setTimeout(() => {
        this.name = '2342345324'
      }, 3000)
    },

    computed: {
      name:{
        get() {
          return this.$store.state.name
        },

        set(value) {
          this.$store.commit('changeName', value)
        }
      }
    }
  }
</script>