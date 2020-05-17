<template>
  <div>
    {{ hhh }}

    <button @click="hhh = 'www'">
      Change 123 to www
    </button>
  </div>
</template>

<script>
export default {
  data: () => ({
    hhh: 123
  }),

  watch: {
    hhh(newValue, oldValue) {
      alert('Вы изменили неправомерно переменную!!!!')
    }
  }
}
</script> 