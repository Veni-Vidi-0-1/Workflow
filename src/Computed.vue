<template>
  <div>
    123321
    {{tascan }}{{jt}}{{dzaybatsu}}
    {{ `${jt} ${dzaybatsu} ${tascan}` }}
  </div>
</template>

<script>
import Evan from '@/Evan.js'

export default {
  computed: {
    tascan() {
      return Evan.tascan
    },

    jt() {
      return Evan.jt
    },

    dzaybatsu() {
      return Evan.dzaybatsu
    }
  }
}
</script> 