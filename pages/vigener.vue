<template>
  <div class="vue">
    <main>
      <nuxt-link to="/">Назад</nuxt-link>
      <h2 align="center" style="margin-top: 15px">Метод Виженера</h2>
      <div class="list">
        <div class="vigener">
          <h5>Шифрование</h5>
          <div class="col-9 container"></div>

          <input
            type="text"
            class="input-site border fs-5 p-2"
            @input="encryption"
            v-model="start_text"
            placeholder="Введите исходный текст"
          />

          <input
            type="text"
            class="input-site border fs-5 p-2"
            @input="encryption"
            v-model="key"
            placeholder="Введите ключ"
          />

          <input
            type="text"
            class="input-site border fs-5 p-2"
            @input="encryption"
            v-model="result"
            placeholder="Результат"
            readonly
          />
        </div>
        <div class="desh">
          <h5>Дешифрование</h5>
          <div class="col-9 container"></div>
          <input
            type="text"
            class="input-site border p-2"
            @input="decryption"
            v-model="finish_text"
            placeholder=" Введите кодированный текст"
          />

          <input
            type="text"
            class="input-site border fs-5 p-2"
            @input="decryption"
            v-model="finish_key"
            placeholder="Введите ключ"
          />

          <input
            type="text"
            class="input-site border fs-5 p-2"
            @input="decryption"
            v-model="finish_result"
            placeholder="Результат"
            readonly
          />
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      start_text: '',
      key: '',
      result: '',
      finish_text: '',
      finish_key: '',
      finish_result: '',
      start_text_gamma: '',
      key_gamma: '',
      result_gamma: '',
      finish_text_gamma: '',
      finish_key_gamma: '',
      finish_result_gamma: '',
      gamma: '',
    }
  },

  methods: {
    encryption() {
      this.result = encryptionFunc(this.start_text, this.key)
    },

    decryption() {
      this.finish_result = decryptionFunc(this.finish_text, this.finish_key)
    },

    encryption_gamma() {
      const gamma = generateRandomKey(this.start_text_gamma.length)
      this.key_gamma = gamma
      this.result_gamma = encryptionGammaFunc(this.start_text_gamma, gamma)
    },

    decryption_gamma() {
      this.finish_result_gamma = decryptionGammaFunc(
        this.finish_text_gamma,
        this.finish_key_gamma
      )
    },
  },
}

function encryptionFunc(start_text, key) {
  start_text = start_text.toUpperCase()
  key = key.toUpperCase()

  var result = ''
  var keyIn = 0

  for (var i = 0; i < start_text.length; i++) {
    var charCode = start_text.charCodeAt(i)

    if (charCode >= 65 && charCode <= 90) {
      var sh = key.charCodeAt(keyIn) - 65
      var encryptedCharCode = ((charCode + sh - 65) % 26) + 65
      result += String.fromCharCode(encryptedCharCode)
      keyIn = (keyIn + 1) % key.length
    } else {
      result += start_text.charAt(i)
    }
  }
  console.log(result)
  return result
}

function decryptionFunc(finish_text, finish_key) {
  finish_text = finish_text.toUpperCase()
  finish_key = finish_key.toUpperCase()

  var result = ''
  var keyIn = 0

  for (var i = 0; i < finish_text.length; i++) {
    var charCode = finish_text.charCodeAt(i)

    if (charCode >= 65 && charCode <= 90) {
      var sh = finish_key.charCodeAt(keyIn) - 65
      var decryptCharCode = ((charCode - sh - 65 + 26) % 26) + 65
      result += String.fromCharCode(decryptCharCode)
      keyIn = (keyIn + 1) % finish_key.length
    } else {
      result += finish_text.charAt(i)
    }
  }

  return result
}

function encryptionGammaFunc(text, key) {
  var result = ''

  for (var i = 0; i < text.length; i++) {
    const charCode = text.charCodeAt(i)
    const keyCh = key.charCodeAt(i % key.length)

    const encryptedCharCode = (charCode + keyCh) % 128
    result += String.fromCharCode(encryptedCharCode)
  }

  return result
}

function decryptionGammaFunc(text, key) {
  var result = ''

  for (var i = 0; i < text.length; i++) {
    const charCode = text.charCodeAt(i)
    const keyCh = key.charCodeAt(i % key.length)

    const decryptedCharCode = (charCode - keyCh + 128) % 128
    result += String.fromCharCode(decryptedCharCode)
  }

  return result
}

function generateRandomKey(length) {
  var key = ''
  const characters =
    'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789'

  for (var i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * characters.length)
    key += characters.charAt(randomIndex)
  }

  return key
}
</script>

<style scoped>
.vue {
  font-family: 'Courier New', Courier, monospace;
  min-height: 100vh;
  color: rgb(15, 14, 14);
  text-align: left;
}

.container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  flex-direction: column;
  align-items: center;
}

.list div {
  margin: 0 auto;
}

input {
  border-radius: 10px;
  width: 500px;
  margin-top: 20px;
  text-align: left;
}

h5 {
  margin-top: 10px !important;
  margin: 10px auto;
}

.vigener {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 15px;
  border: 2px solid black;
  background-color: #e9b872;
  border-radius: 15px;
  width: 700px;
}

.desh {
  margin-top: 10px !important;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 15px;
  border: 2px solid black;
  background-color: #e9b872;
  border-radius: 15px;
  width: 700px;
}
</style>
<style>
body {
  font-family: 'Courier New', Courier, monospace;
  background-color: #bbc7ce;
}
</style>
