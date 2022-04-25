<template>
<div>
  <p>
    {{ randomSentence }}
  </p>
</div>
</template>

<script>
// @ is an alias to /src
import Sentences from '@/assets/sentences.json'
export default {
  name: 'Home',
  data () {
    return {
      sentences: Sentences
    }
  },
  computed: {
    introductions () {
      return Sentences.introductions
    },
    persons () {
      return Sentences.persons
    },
    backgrounds () {
      return Sentences.backgrounds
    },
    places () {
      return Sentences.places
    },
    settings () {
      return Sentences.settings
    },
    locations () {
      return Sentences.locations
    },
    verbs () {
      return Sentences.verbs
    },
    foods () {
      return Sentences.foods
    },
    middlePart () {
      return Sentences.foods
    },
    randomSentence () {
      const keys = [
        'introductions',
        'persons',
        'backgrounds',
        'places',
        'settings',
        'locations',
        'verbs',
        'foods',
        'moods1',
        'moods2'
      ]
      let sentence = ''
      keys.map(e => {
        sentence += this.shuffle(Sentences[e])[0]
        if (e === 'foods') {
          sentence += '. '
        } else {
          sentence += ' '
        }
      })
      return sentence
    }
  },
  methods: {
    // Fisher Yates
    shuffle (input) {
      const a = input
      const aLength = a.length
      for (var i = aLength - 1; i >= 0; i--) {
        var randomIndex = Math.floor(Math.random() * (i + 1))
        var itemAtIndex = a[randomIndex]
        a[randomIndex] = a[i]
        a[i] = itemAtIndex
      }
      return a
    }
  }
}
</script>
