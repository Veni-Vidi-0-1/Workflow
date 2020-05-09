<template>
  <div>
    <div
      v-kinglamba
      v-evan
      v-yuma
    >
      Im not Red text
    </div>
    <button
      v-kinglamba
      v-taskan
      v-dzaybatsu="50"
    >
      КНОПОШКА
    </button>
  </div>
</template>

<script>
  export default {
    directives: {
      dzaybatsu: {
        inserted: function (el, payload) {
          console.log(payload.value)
        }
      },
      
      kinglamba: {
        inserted: function (el) {
          el.style.color = 'red'
        }
      },
      
      yuma: {
        inserted: function(el) {
          const imageUrl = 'https://img.imgsmail.ru/pkgs/otvet-static/static/i/images/logo_v2/logo.png'
          let pic = document.createElement('img')
          pic.src = imageUrl 
          el.appendChild(pic)
        }
      },

      evan: {
        inserted: function(el) {
          el.textContent = el.textContent.split('').reverse().join('')
        }
      },

      taskan: {
        inserted: function (el) {
          el.onclick = () => {
            window.location.reload()
          }
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  button {
    background: linear-gradient(45deg, black 10%, transparent 50%, black 40%);
    padding: 20px;
    color: white;
    border-radius: 15px;
    transition: all 0.2s ease-in-out;
    border: 10px double transparent;
    &:hover {
      background: linear-gradient(65deg, black 40%, transparent 50%, black 10%);
    }
    &:active {
      font-size: 90px;
    }
  }
</style>