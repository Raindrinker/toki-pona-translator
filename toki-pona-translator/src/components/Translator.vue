<template>
  <div class="translator">
    <img src="../assets/toki_pona_logo.png" class="logo">
    <div class="bg-accent">

    </div>
    <div class="accent-content">
      <a href="https://tokipona.org/">toki pona made by sonja lang</a>
      <a href="https://twitter.com/Raindrinker_dev">website made by mi moku e telo kon</a>
    </div>
    <div class="translate-card">
        <div class="translator-block source">
          <div class="translator-block-header">
            TOKI PONA
          </div>
          <div class="translator-block-body">
            <textarea rows="10" v-model="input" @input="updateInput"></textarea>
          </div>
          <div class="translator-block-body analysis-output">
            <AnalysisOutput :output="output"/>
          </div>
        </div>
        <div class="translator-block dest">
          <div class="translator-block-header">
            ENGLISH
          </div>
          <div class="translator-block-body">
            <TranslationOutput :output="output"/>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
import TPEnglish from "../utils/tokipona-english"
import TranslationOutput from "./TranslationOutput";
import AnalysisOutput from "./AnalysisOutput";

export default {
  name: 'Translator',
  components: {AnalysisOutput, TranslationOutput},
  data() {
    return {
      input: "",
      output: {}
    }
  },
  methods: {
    updateInput() {
      this.output = TPEnglish.getTextTranslation(this.input);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.translator {

  width: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;

  position: relative;

}

.logo {
  height: 80px;
  width: auto;
  padding: 32px;
}

.translate-card {
  width: 80%;
  display: flex;
  flex-direction: row;

  border-radius: 8px;
  box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.4);
  background-color: white;
}

.translator-block-header {
  display: flex;
  padding: 16px;
  border-bottom: 1px solid lightgray;
  font-weight: bold;
}

.translator-block-body {
  padding: 16px;
}

.output-text {

  font-size: 16pt;
  text-align: start;
  font-family: Arial,sans-serif;
}

textarea {
  resize: none;
  width: 100%;
  border: none;
  outline: none;
  background-color: transparent;

  font-size: 16pt;
  font-family: Arial,sans-serif;
}

.translator-block {
  flex-grow: 1;
  flex-basis: 50%;
  flex-shrink: 1;
}

.translator-block.source {
  border-right: 1px solid lightgray;
}

.translator-block.dest {
  background-color: #F0F0F0;
}

.bg-accent {
  height: 175px;
  background-color: #FFFF63;
  position: absolute;
  width: 100%;
  z-index: -1;
  border-bottom: 1px solid lightgray;

}

.accent-content {
  position: absolute;
  pointer-events: all;
  right: 0px;
  padding: 8px;
  font-weight: bold;
  opacity: 0.3;
  display: flex;
  flex-direction: column;
  align-items: end;
}

a {
  text-decoration: none;
  color: black;
}

a:active {

}

.analysis-output {
  height: 100px;
  background-color: #F0F0F0;
  border-top: 1px solid lightgray;
}

</style>
