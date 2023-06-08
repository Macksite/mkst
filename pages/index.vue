<template>
  <div class="page">
    <div class="input-container">
      <div class="input-wrapper">
        <label for="input">非迫真テキスト</label>
        <input id="input" v-model="inputText" type="text" class="custom-input" />
      </div>
      <button @click="processInput" class="neumorphism-button">（迫真）</button>
    </div>
    <div class="form">
      <label for="output">迫真テキスト</label>
      <transition name="textarea-transition">
        <textarea
          id="output"
          ref="outputTextarea"
          :class="{ 'textarea-transition': shouldAnimate }"
          :style="{ height: outputHeight + 'px' }"
          v-model="outputText"
          readonly
        ></textarea>
      </transition>
    </div>
  </div>
</template>

<style scoped>
.input-wrapper {
  flex: 1;
  margin-right: 10px;
}

.input-container {
  align-self: flex;
  background-color: rgb(255, 255, 255);
  box-shadow: 6px 6px 10px #ffbaed;
  padding: 8px 16px;
  border-radius: 20px;
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.custom-input {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  background-color: rgb(233, 236, 247);
  border: none;
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
  border: aquamarine;
  border-radius: 10px;
  padding: 10px 2px;
}

.neumorphism-button {
  margin-top: 24px;
  background-color: #f0f3f8;
  border: none;
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

.form {
  background-color: rgb(255, 255, 255);
  border: none;
  border-radius: 10px;
  box-shadow: 6px 6px 10px #9ed5fc;
  padding: 10px;
  margin-bottom: 100px;
}

#output {
  background-color: #c7ffd3;
  border-radius: 15px;
  border: none;
  display: table;
  resize: none;
  overflow: hidden;
  font-size: 16px;
  transition: 0.2s;
}

.textarea-transition-enter-active,
.textarea-transition-leave-active {
  transition: 0.2s;
}

.textarea-transition-enter,
.textarea-transition-leave-to {
  height: 0 !important;
}
</style>

<script>
export default {
  data() {
    return {
      inputText: "",
      outputText: "",
      outputHeight: 0,
      shouldAnimate: false
    };
  },
  methods: {
    processInput() {
      
      const processedText = this.inputText
        .split("")
        .map(char => char + "　")
        .join("");

      this.outputText = processedText;
      this.updateOutputHeight();
    },
    calculateRows(text) {
      const lines = text.split("\n");
      const maxLength = Math.max(...lines.map(line => line.length));
      const rows = Math.max(lines.length, 4);

      if (maxLength <= 1) {
        return rows;
      } else {
        return Math.ceil(rows * (maxLength / 10));
      }
    },
    updateOutputHeight() {
      this.$nextTick(() => {
        const textarea = this.$refs.outputTextarea;
        if (textarea) {
          textarea.style.height = "auto";
          textarea.style.height = textarea.scrollHeight + "px";
          this.outputHeight = textarea.scrollHeight;

          // アニメーションの開始を遅延させるため、shouldAnimateプロパティを設定します
          this.shouldAnimate = true;
          setTimeout(() => {
            this.shouldAnimate = false;
          }, 5000);
        }
      });
    }
  },
  watch: {
    outputText() {
      this.updateOutputHeight();
    }
  }
};
</script>