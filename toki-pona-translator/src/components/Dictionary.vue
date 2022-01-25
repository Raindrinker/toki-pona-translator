<template>
  <div class="dictionary">
    <div class="content">
    <div class="title">
      <img src="../assets/book.png" class="logo">DICTIONARY
    </div>
    <div v-for="word in Object.keys(dict)" :key="word" class="word-row">
      <div class="tokipona-glyph">
        <img :src="getGlyphUrl(word)" class="tokipona-glyph-img" onerror="this.style.display='none'">
      </div>
      <div class="tokipona-word">
        {{word}}
      </div>
      <div class="meanings">
        <div class="noun meaning-row" v-if="dict[word].noun"><div class="type">n</div> {{dict[word].noun}}
        </div>
        <div class="modifier meaning-row" v-if="dict[word].modifier"><div class="type">mod</div> {{dict[word].modifier}}
        </div>
        <div class="modifier meaning-row" v-if="dict[word].verb_transitive"><div class="type">vt</div> {{dict[word].verb_transitive}}
        </div>
        <div class="modifier meaning-row" v-if="dict[word].verb_intransitive"><div class="type">vi</div> {{dict[word].verb_intransitive}}
        </div>
        <div class="modifier meaning-row" v-if="dict[word].interjection"><div class="type">interj</div> {{dict[word].interjection}}
        </div>
        <div class="modifier meaning-row" v-if="dict[word].conjunction"><div class="type">conj</div> {{dict[word].conjunction}}
        </div>
        <div class="modifier meaning-row" v-if="dict[word].separator"><div class="type">sep</div> {{dict[word].separator}}
        </div>
        <div class="modifier meaning-row" v-if="dict[word].special"><div class="type">special</div> {{dict[word].special}}
        </div>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import TPEnglish from "../utils/tokipona-english"

export default {
  name: "Dictionary",
  data() {
    return {
      dict: TPEnglish.getDict()
    }
  },
  methods: {
    getGlyphUrl(word) {
      return '/img/sitelen/' + word + ".svg";
    }
  }
}
</script>

<style scoped>

.dictionary {
  margin-top: 32px;

  display: flex;
  align-items: center;
  justify-content: center;
}

.content {
  width: 80%;
}

.word-row {
  display: flex;
  padding: 12px;
}

.tokipona-word {
  flex-basis: 120px;
  font-weight: bold;

  display: flex;
  align-items: center;
  justify-content: start;
}

.tokipona-glyph {
  display: flex;
  align-items: center;
  margin-right: 16px;
  width: 32px;
}

.tokipona-glyph-img {
  height: 32px;
}

.meanings {
  display: flex;
  flex-direction: column;
  align-items: start;
}

.meaning-row {
  display: flex;
  padding: 4px;
}

.type {
  font-weight: bold;
  color: #888888;
  width: 80px;
  text-align: start;
}

.title {
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;

  border-bottom: 1px solid lightgrey;
  padding-bottom: 8px;
  margin-bottom: 32px;
}

.logo {
  height: 32px;
  padding-right: 16px;
  opacity: 0.8;
}
</style>