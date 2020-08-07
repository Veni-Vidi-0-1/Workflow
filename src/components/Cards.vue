<template>
  <div>
    <audio
      ref="audio"
      class="hidden-audio"
    />
  </div>
</template>

<script>
import * as ex from 'excalibur'

let game,
bozhenka,
katamaranov,
starozubov,
ingener,
victor_sergeich

export default {
  data: () => ({
    card: {
      width: 310,
      height: 440
    },

    total: 10
  }),

  mounted() {
    this.initGame()
  },
  
  methods: {
    initGame() {
      game = new ex.Engine({
        width: document.body.clientWidth,
        height: document.body.clientHeight
      })

      bozhenka = new ex.Texture('/img/bozhenka.png')
      katamaranov = new ex.Texture('/img/katamaranov.png')
      starozubov = new ex.Texture('/img/starozubov.png')
      ingener = new ex.Texture('/img/Инженер 1.png')
      victor_sergeich = new ex.Texture('/img/victor_sergeich.png')

      const loader = new ex.Loader([
        bozhenka,
        katamaranov,
        starozubov,
        ingener,
        victor_sergeich
      ])

      game.start(loader)

      this.setCards()
    },

    setCards() {
      this.createCard(
        150,
        150,
        bozhenka,
        '/audio/roza 1.mp3'
      )
      
      this.createCard(
        450,
        150,
        katamaranov,
        '/audio/sdohumer 1.mp3'
      )
      
      this.createCard(
        150,
        450,
        starozubov,
        '/audio/uaz 1.mp3'
      )

      this.createCard(
        450,
        450,
        ingener,
        '/audio/jurn 1.mp3'
      )

      this.createCard(
        750,
        750,
        victor_sergeich,
        '/audio/inj 1.mp3'
      )
    },

    createCard(x, y, texture, audio) {
      const paddle = new ex.Actor(x, y, this.card.width, this.card.height)
      paddle.collisionType = ex.CollisionType.Fixed
      paddle.addDrawing(texture)
      // paddle.draggable = true
      paddle.onInitialize = () => {
        paddle.isMove = false

        paddle.on(ex.EventTypes.PointerMove, (e) => {
          if(!paddle.isMove) return
          paddle.pos.setTo(e.pos.x, e.pos.y)
        })

        paddle.on(ex.EventTypes.PointerDown, (e) => {
          // @TODO при первом клике на одну из первых карточек - в ебеня исчезает другая
          if (paddle.isMove) {
            this.$refs.audio.src = audio
            this.$refs.audio.play()
            paddle.isPlayed = true
            setTimeout(() => {
              paddle.isPlayed = false
            }, 900)
          }

          paddle.isMove = !paddle.isMove
        })
      }

      game.add(paddle)
    }
  }
}
</script>

<style scoped>
  .hidden-audio {
    opacity: 0;
  }
</style>
