
<template>
  <div class="mordova">
    {{ name | taskanFilter }}
    <br />
    {{ name | generateNickName }}
    <br />
    {{ name | reverseText }}
  </div>
</template>

<script>
  export default {
    filters: {
      taskanFilter(value) {
        value = value.toUpperCase()
        return value
      },

      generateNickName(value) {
        value = value.toLowerCase().split(' ').join('_') //.join(" ._. ")
        return value  // Json Stathem => json_stathem
      },

      reverseText(value) {
        value = value.split('').reverse().join('')
        return value
      }
    },

    data: () => ({
      name: 'Json Stathem'
    })
  }
</script>


<style scoped>
.mordova{
    margin-top : 8%;
    padding: 50px;
    border: 10px double blue;
}
</style>
