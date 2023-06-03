<template>
  
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <NuxtLogo />
        <VuetifyLogo />
      </v-card>
      <v-card>
        <v-card-title class="headline">
          Welcome to the Vuetify + Nuxt.js template
        </v-card-title>
        <div>
    <div class="input-container">
      <label for="input">入力フォーム</label>
      <input id="input" v-model="inputText" type="text" />
    </div>
    <div>
      <label for="output">出力フォーム</label>
      <textarea id="output" rows="4" cols="50" v-model="outputText" readonly></textarea>
    </div>
    <button @click="processInput" class="neumorphism-button">（迫真）</button>
  </div>
        <v-card-text>
          <p>Vuetify is a progressive Material Design component framework for Vue.js. It was designed to empower developers to create amazing applications.</p>
          <p>
            For more information on Vuetify, check out the <a
              href="https://vuetifyjs.com"
              target="_blank"
              rel="noopener noreferrer"
            >
              documentation
            </a>.
          </p>
          <p>
            If you have questions, please join the official <a
              href="https://chat.vuetifyjs.com/"
              target="_blank"
              rel="noopener noreferrer"
              title="chat"
            >
              discord
            </a>.
          </p>
          <p>
            Find a bug? Report it on the github <a
              href="https://github.com/vuetifyjs/vuetify/issues"
              target="_blank"
              rel="noopener noreferrer"
              title="contribute"
            >
              issue board
            </a>.
          </p>
          <p>Thank you for developing with Vuetify and I look forward to bringing more exciting features in the future.</p>
          <div class="text-xs-right">
            <em><small>&mdash; John Leider</small></em>
          </div>
          <hr class="my-3">
          <a
            href="https://nuxtjs.org/"
            target="_blank"
            rel="noopener noreferrer"
          >
            Nuxt Documentation
          </a>
          <br>
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
            rel="noopener noreferrer"
          >
            Nuxt GitHub
          </a>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/inspire"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>
<style scoped>
.input-container {
  background-color: white;
  border-radius: 5px;
  border: 2px solid skyblue;
  padding: 10px;
}

.custom-input {
  width: 100%;
  padding: 5px;
  font-size: 16px;
}
.neumorphism-button {
  /* ニューモーフィズムボタンのスタイル */
  background-color: #f0f3f8;
  border: none;
  border-radius: 10px;
  box-shadow: 6px 6px 10px #c7d1e1, -6px -6px 10px #ffffff;
  padding: 10px 20px;
  font-size: 16px;
  color: #333;
  cursor: pointer;
  transition: all 0.3s ease;
}

.neumorphism-button:hover {
  box-shadow: 2px 2px 5px #c7d1e1, -2px -2px 5px #ffffff;
  transform: translate(2px, 2px);
}

.neumorphism-button:active {
  box-shadow: inset 1px 1px 2px #c7d1e1, inset -1px -1px 2px #ffffff;
  transform: translate(1px, 1px);
}
</style>


<script>

export default {
  data() {
    return {
      inputText: "",
      outputText: ""
    };
  },
  methods: {
    processInput() {
      const processedText = this.inputText
        .split("") // 文字列を一文字ずつの配列に分割
        .map(char => char + "　") // 全角スペースを追加
        .join(""); // 配列を文字列に結合

      this.outputText = processedText;
    }
  },
  name: 'IndexPage'
  
}

</script>

