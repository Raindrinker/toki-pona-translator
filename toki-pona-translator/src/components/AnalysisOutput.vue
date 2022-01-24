<template>
  <div class="output-text">
    <template v-if="output.translation">
      <div class="sentence" v-for="(sentence, index) in output.analysis.sentences" :key="index">
        <template v-if="sentence.is_text">
          <div class="subject">
            <div class="word" v-for="(word, index) in sentence.subject" :key="index">
              {{word}}<span v-if="index !== sentence.subject.length - 1">&nbsp;</span>
            </div>
          </div>
          <div v-if="sentence.has_verb" class="verb">&nbsp;li&nbsp;
            <div class="word" v-for="(word, index) in sentence.verb" :key="index">
              {{word}}<span v-if="index !== sentence.verb.length - 1">&nbsp;</span>
            </div>
          </div>
          <div v-if="sentence.has_object" class="object">&nbsp;e&nbsp;
            <div class="word" v-for="(word, index) in sentence.object" :key="index">
              {{word}}<span v-if="index !== sentence.object.length - 1">&nbsp;</span>
            </div>
          </div>
          </template>
        <template v-else>
          {{sentence.content}}
          <span v-if="index !== output.translation.sentences.length - 1">&nbsp;</span>
        </template>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "AnalysisOutput",
  props: {
    output: Object
  }
}
</script>

<style scoped>
.sentence, .subject, .verb, .object, .output-text{
  display: flex;
}

.subject .word {
  background-color: lightblue;
}

.verb .word {
  background-color: lightgreen;
}

.object .word {
  background-color: pink;
}
</style>