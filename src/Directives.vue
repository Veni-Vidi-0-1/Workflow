<template>
  <div class="w1-section">
    <button v-uwu>
      Test button
    </button>
  </div>
</template>

<script>
export default {
  directives: {
    uwu: {
      bind: function(el, binding, vnode) {
        vnode.context.privet()
      }
    }
  },

  methods: {
    privet() {
      console.log('привет uwu')
    }
  }
}
</script>