<template>
  <div class="w1-section">
    <div class="w1-fixed">
      Видим ли мы элемент: {{ isVisible ? 'Видимый' : 'Невидимый' }}
    </div>
    <div
      class="w1-bottom-text"
      ref="img"
    >
      Элемент в середочке
      <img
        v-if="isVisible"
        src="https://i.ytimg.com/vi/b0ecKLOOzJc/hqdefault.jpg"
        width="500"
      >
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    isVisible: false
  }),
  
  mounted() {
    this.initObserver()
  },

  methods: {
    initObserver() {
      const observer = new IntersectionObserver(this.observeImage, {
        rootMargin: '0px',
        threshold: 0.1
      })
      
      const target = this.$refs.img
      if (target) observer.observe(target)
    },

    observeImage(entries, observer) {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          this.isVisible = true
        } else {
          this.isVisible = false
        }
      })
    }
  }
  
}
</script>


<style>
  .w1-section {
    position: relative;
    height: 4000px;
    width: 100%;
  }

  .w1-fixed {
    position: fixed;
    top: 100px;
    left: 100px;
  }

  .w1-bottom-text {
    margin-top: 3800px;
  }
</style>