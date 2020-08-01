<template>
  <div>
    <button @click="startRecord">
      Начать запись
    </button>
    <button @click="stopRecord">
      Оставновить и скачать запись
    </button>
  </div>
</template>

<script>
import { saveAs } from 'file-saver'

let record = {}
let streamData = []

export default {
  data: () => ({
    record2: []
  }),

  methods: {
    startRecord() {
      navigator.mediaDevices.getDisplayMedia({
        video: {
          cursor: 'always'
        },
        audio: {
          echoCancellation: true,
          noiseSuppression: true,
          sampleRate: 50000
        }
      }).then(stream => {
        record = new MediaRecorder(stream, {
          mimeType: 'video/webm;codecs=vp9'
        })

        streamData = []

        record.ondataavailable = e => {
          streamData.push(e.data)
        }

        record.onstop = () => {
          let fileName = 'veni-vidi-record-0000'

          let blob = new Blob(streamData, { type: 'video/webm' })
          
          let file = new File([blob], `${fileName}.webm`, { type: 'video/webm' })

          saveAs(file)
        }

        record.onerror = (e) => {
          console.log(e)
        }

        record.start(1000)
      })
    },

    stopRecord() {
      record.stop()
    }
  }
}
</script>