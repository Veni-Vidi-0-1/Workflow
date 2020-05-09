<template>
  <div
    v-on="$listeners"
    class="kinglamba"
  >
    <div v-text="one" />
    <div>{{ two ? 'Да' : 'Нет' }}</div>
    <div>
      <ul>
        <li
          v-for="(item, key) in three"
          @click="number(item)"
          :key="key"
        >
          {{ item }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    one: {
      type: String,
      default: () => ''
    },
    
    two: {
      type: Boolean,
      default: () => true,
    },
    
    three: {
      type: Array,
      default: () => []
    }
  },
  
  methods: {
    number(num) {
      this.$emit('test-event', num)
    }
  }
}
</script>

<style scoped>
  .kinglamba {
    background: black;
    color: white;
    border: 10px double red;
    padding: 50px;
  }
</style>
