<template>
  <div>
    <div class="page-container">
     <div class="input-container">
       <div class="input-wrapper">
         <label for="input">入力フォーム</label>
         <input id="input" v-model="inputText" type="text" class="custom-input" />
       </div>
       <button @click="processInput" class="neumorphism-button">（迫真）</button>
     </div>
    <div>
      <label for="output">出力フォーム</label>
      <textarea id="output" rows="4" cols="50" v-model="outputText" readonly></textarea>
    </div>
  </div>
  </div>
</template>
<style scoped>
.input-wrapper {
  flex: 1;
  margin-right: 10px;
}

.page-container {
  background-color: white;
}

.input-container {
  background-color: white;
  border-radius: 5px;
  border: 2px solid skyblue;
  padding: 10px;
    display: flex;
  align-items: center;
  margin-bottom: 20px;
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

