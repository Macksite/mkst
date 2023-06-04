<template>
  <div class="page-container">
    <div >
     <div class="input-container">
       <div class="input-wrapper">
         <label for="input">非迫真テキスト</label>
         <input id="input" v-model="inputText" type="text" class="custom-input" />
       </div>
       <button @click="processInput" class="neumorphism-button">（迫真）</button>
     </div>
    <div class="output">
      <label for="output">迫　真　テ　キ　ス　ト</label>
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

.page-container{
  background-color: rgb(255, 255, 255); 
}

.input-container {
  align-self:flex-end;
  background-color: white;
  border: none;
  border-radius: 10px;
  box-shadow: 6px 6px 10px #ffcaf2, -6px -6px 10px #a5ffc9;
  padding: 10px;
    display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.custom-input {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  background-color: #e1e6f0;
  border: none;
  border-radius: 10px;
  padding: 10px 20px;
  cursor: pointer;
  transition: all 0.3s ease;
}
.custom-input:active {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  background-color: #d6dff3;
  border: none;
  border-radius: 10px;
  padding: 10px 20px;
}
.custom-input:hover {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  background-color: #dde4ff;
  border: none;
  border-radius: 10px;
  padding: 10px 20px;
}
.neumorphism-button {
  /* ニューモーフィズムボタンのスタイル */
  background-color: #f0f3f8;
  border: none;
  border-radius: 10px;
  box-shadow: 6px 6px 10px #9be6ed, -6px -6px 10px #ffffff;
  padding: 10px 10px;
  font-size: 16px;
  color: hsl(0, 0%, 0%);
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
.output{
  background-color: rgb(255, 255, 255);
  border: none;
  border-radius: 10px;
  box-shadow: 6px 6px 10px #b1cfff, -6px -6px 10px #ffffff;
  padding: 10px;
  display:-moz-popu;
  align-items:baseline;
  margin-bottom: 20px;
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

