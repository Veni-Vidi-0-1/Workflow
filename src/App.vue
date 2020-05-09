<template>
  <div class="app">
    <KingLamba
      @test-event="testFunction"
      :one="one"
      :two="two"
      :three="three"
    />
  
    <Mordova />
    <Evan />


    <Tascan>
      Hello Andrey
      <img src='https://static.mk.ru/upload/entities/2018/11/29/articles/detailPicture/17/4c/ae/d0/d6427b87abed19c359658a5d858157e1.jpg'>
      Some more text
      <input>
      <textarea>23423</textarea>
    </Tascan>
  </div>
</template>

<script>
import KingLamba from '@/components/KingLamba.vue'
import Mordova from '@/components/Mordova.vue'
import Evan from '@/components/Evan.vue'
import Tascan from '@/components/Tascan.vue'

export default {
  components: {
    KingLamba,
    Mordova,
    Evan,
    Tascan
  },

  data: () => ({
    one: 'Строка',
    two: false,
    three: [
      1, 2, 3, 4
    ]
  }),
  
  methods: {
    testFunction(testValue) {
      console.log(`Событие из App.vue: ${testValue}`)
    },

    clickFunction(event) {
      alert(event)
    }
  }
}
</script>


<style>
  body {
    margin: 0;
    padding: 0;
  }

  .app {
    width: 100%;
    height: 100%;
    background-image: url('https://static.mk.ru/upload/entities/2018/11/29/articles/detailPicture/17/4c/ae/d0/d6427b87abed19c359658a5d858157e1.jpg');
    background-size: 100%;
  }
</style>