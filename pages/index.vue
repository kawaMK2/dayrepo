<template lang="pug">
  section.container
    h1 日報つくるくん
    p 五省フォーマット形式の日報が作れるやつ by石嶺

    div.row
      div.col-md-7
        div.card
          div.card-header
            h5.card-title ▼1：今日1日の自分と向き合って振り返って、内省してみよう
          div.card-body
            form
              yes-no-input(:value="five_reflections.sincerity" @input="five_reflections.sincerity = $event.value")
              p {{five_reflections.sincerity}}
      div.col-md-5
        div.card
          div.card-header
            h4.card-title 出力結果
          div.card-body
            textarea(readonly :rows="rows").form-control.result {{resultText}}
</template>

<script>
import YesNoInput from '~/Components/YesNoInput.vue'

export default {
  components: {
    YesNoInput
  },
  data: function() {
    return {
      five_reflections: {
        sincerity: null,
        no_ashamed_to_word: null,
        no_lacked_to_vigor: null,
        exerted_efforts: null,
        not_become_slothful: null
      }
    }
  },
  computed: {
    resultText: function() {
      const fr = this.five_reflections
      const frResult =
        '\n１）真心を持って人に接していたか\t' +
        fr.sincerity +
        '\n２）嘘をつかず、言行不一致な点はなかったか\t' +
        fr.no_ashamed_to_word +
        '\n３）十分な精神力を持って、人や仕事、困難に向き合えたか\t' +
        fr.no_lacked_to_vigor +
        '\n４）難を乗り越えるために十分に努力し本気で汗をかいたか\t' +
        fr.exerted_efforts +
        '\n５）怠けたりさぼったりせず、最後まで真剣に取り組んだか \t' +
        fr.not_become_slothful +
        '\n'
      return frResult
    },
    rows: function() {
      const num = this.resultText.split('\n').length
      return num > 4 ? num : 4
    }
  }
}
</script>

<style>
.container {
  padding: 50px;
  font: 14px 'Lucida Grande', Helvetica, Arial, sans-serif;
}

.result {
  font-size: 12px;
}

a {
  color: #00b7ff;
}

h1,
h2 {
  font-weight: 100;
}

h1 {
  font-size: 35px;
}

ul li {
  padding: 5px;
}
</style>
