<template>
  <div class="page">
    <div>
     <div class="input-container">
       <div class="input-wrapper">
         <label for="input">非迫真テキスト</label>
         <input id="input" v-model="inputText" type="text" class="custom-input" />
       </div>
       <button @click="processInput" class="neumorphism-button">（迫真）</button>
     </div>
    <div class="form">
      <label for="output">迫　真　テ　キ　ス　ト</label>
       <transition name="textarea-transition">
       <textarea id="output" :rows="calculateRows(outputText)" cals="50" v-model="outputText" readonly>
       </textarea>
      </transition>
    </div>

  </div>
  </div>
</template>

<style scoped>
.input-wrapper {
  flex: 1;
  margin-right: 10px;

}

.input-container {
  align-self:flex;
  background-color: rgb(255, 255, 255);
  box-shadow: 6px 6px 10px #ffbaed;
  padding: 8px 16px; /* ボタンの余白を設定する */
  border-radius: 20px; /* 角丸を設定する */
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.custom-input {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  background-color: rgb(233, 236, 247);
  border:none;
  border-radius: 10px;
  padding: 10px 2px;
  cursor: pointer;
  transition: all 0.1s ease;
}

.custom-input:hover {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  background-color: #dde4ff;
  border:aquamarine;
  border-radius: 10px;
  padding: 10px 2px;
}
.neumorphism-button {
  /* ニューモーフィズムボタンのスタイル */
  margin-top: 24px;
  background-color: #f0f3f8;
  border:none;
  border-radius: 10px;
  padding: 10px 10px;
  font-size: 16px;
  color: hsl(0, 0%, 0%);
  cursor: pointer;
  transition: all 0.1s ease;
}

.neumorphism-button:hover {
background-color: #c7ffd3;
}

.neumorphism-button:active {
  background-color: #dcfffd;
  }
.form{
  background-color: rgb(255, 255, 255);
  border: none;
  border-radius: 10px;
  box-shadow: 6px 6px 10px #9ed5fc;
  padding: 10px;
  margin-bottom: 100px;
}

#output {
  background-color: #c7ffd3; /* デフォルトのブロック要素として表示する */
  border-radius: 15px;
  border:none;
  display:table; /* デフォルトのブロック要素として表示する */
  resize: none; /* ユーザーによるリサイズを禁止する */
  overflow: hidden;
  font-size: 16px;
}

.textarea-transition-enter-active,
.textarea-transition-leave-active {
  transition: height 0.5s;
}

.textarea-transition-enter,
.textarea-transition-leave-to {
  height: 0;
  opacity: 0;
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
      
    },
    calculateRows(text) {
      const lines = text.split("\n"); // 改行文字で分割
      const maxLength = Math.max(...lines.map(line => line.length)); // 各行の最大文字数を取得
      const rows = Math.max(lines.length, 4); // 行数を計算（最低でも4行にする）

      // 最大文字数に応じて行の高さを調整
      if (maxLength <= 50) {
        return rows;
      } else {
        return Math.ceil(rows * (maxLength / 50));
      }
    },
    updateOutputHeight() {
      const textarea = this.$refs.outputTextarea;
      if (textarea) {
        this.outputHeight = `${textarea.scrollHeight}px`;
      }
    }
  },
  
  };
  name: 'IndexPage'
  
</script>