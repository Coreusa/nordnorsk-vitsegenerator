<template>
<div class="row">
  <div class="col-12 col-md-4 mx-auto bg-light p-3 rounded">
    <img
      src="/images/logo.jpg"
      class="w-100 mb-3"
    />
    <h1>{{ generatedStoryHeading }}</h1>
    <p>
      {{ generatedStory }}
    </p>
    <button
      @click="createStory()"
      class="btn btn-success btn-sm"
    >
      Ny vits, takk!
    </button>

  </div>
</div>
</template>

<script>
// @ is an alias to /src
import Sentences from '@/assets/sentences.json'
export default {
  name: 'Home',
  data () {
    return {
      sentences: Sentences,
      generatedStoryHeading: '',
      generatedStory: ''
    }
  },
  computed: {
    storyHeadings () {
      return {
        story1: [
          'storyName1',
          'storyName2',
          'storyName3'
        ],
        story2: [
          'storyName1',
          'storyName2',
          'storyName3'
        ],
        story3: [
          'storyName1',
          'storyName2',
          'storyName3'
        ],
        story4: [
          'adjectives5',
          'adjectives6'
        ]
      }
    },
    story1 () {
      return [
        'introductions',
        'persons',
        'backgrounds',
        'places1',
        '. ',
        'settings',
        'locations',
        ' og ',
        'verbs',
        'foods',
        '. ',
        'moods1',
        'moods2',
        ' Plutselig ',
        'surprises1',
        ', og ',
        'surpriseActors',
        'surpriseActorActions',
        '. ',
        '"',
        'exclamations1',
        'exclamations2',
        '"',
        ' utbraut ',
        'persons',
        'surpriseActions',
        '.',
        'silences',
        'postSilences',
        'persons',
        'postSilenceDescriptions',
        'exclamations3',
        ' at ',
        'exclamations4',
        'tonalIntentions',
        'exclamations5',
        '" '
      ]
    },
    story2 () {
      return [
        'introductions',
        'persons',
        'backgrounds',
        'places1',
        '. Folk va samla tell ',
        'places2',
        ' i ',
        'locations',
        ', og ',
        'exclamations4',
        'supplementals1',
        '. ',
        'moods1',
        ' helt tell han Teodor reist sæ opp, kræmta og ba om orde: "',
        'dialogues1',
        '! Det e ikkje kvær dag man får gaffel i sæ ',
        'adjectives4',
        'foods',
        ' ilag me ',
        'exclamations4',
        '. ',
        'dialogues2',
        '"',
        'silences',
        'postSilences',
        'persons',
        ', ',
        'postSilenceDescriptions',
        '" Teodor, din ',
        'adjectives1',
        'adjectives2',
        'adjectives3',
        ', ',
        'exclamations6',
        '"'
      ]
    },
    story3 () {
      return [
        'Det va ',
        'places2',
        'places1',
        '.',
        'settings',
        'locations',
        ' og åt ',
        'adjectives4',
        'foods',
        '. Plutselig fikk de øye på ',
        'exclamations4',
        ' som kom sprenganes me ',
        'things1',
        ' i nævan.',
        'exclamations1',
        '..!\' kauka ',
        'persons',
        ', \'-',
        'exclamations2',
        'silences',
        'postSilences',
        'persons',
        ',',
        'postSilenceDescriptions',
        '\' Der kan dokk sjå. Når det ',
        'verbs2',
        'foods',
        ' i ',
        'locations',
        ', ',
        'exclamations7',
        '!'
      ]
    },
    story4 () {
      return [
        'introductions',
        'persons',
        'backgrounds',
        'places1',
        '. ',
        'settings',
        'locations',
        ' og ',
        'verbs',
        'foods',
        '. ',
        'moods1',
        'moods2',
        'Plutselig ',
        'surprises1',
        ', og ',
        'surpriseActors',
        'surpriseActorActions',
        '.',
        'exclamations1',
        '... ',
        'exclamations2',
        'utbraut ',
        'persons',
        'surpriseActions',
        '. ',
        'silences',
        'postSilences',
        'persons',
        ', ',
        'postSilenceDescriptions',
        'exclamations3',
        ' at ',
        'exclamations4',
        'tonalIntentions',
        'exclamations5'
      ]
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
    },
    createStory () {
      const situations = [
        this.story1,
        this.story2,
        this.story3,
        this.story4
      ]
      const headingKeys = Object.keys(this.storyHeadings)
      const randomStoryHeading = headingKeys[Math.floor(Math.random() * headingKeys.length)]

      const randomStory = situations[Math.floor(Math.random() * situations.length)]
      let story = ''
      let storyHeading = ''
      this.storyHeadings[randomStoryHeading].map(e => {
        storyHeading += this.shuffle(Sentences[e])[0] + ' '
      })
      this.generatedStoryHeading = storyHeading
      randomStory.map(e => {
        if (Sentences[e] !== undefined) {
          story += this.shuffle(Sentences[e])[0] + ' '
        } else {
          story += e
        }
      })
      this.generatedStory = story
    }
  },
  created () {
    this.createStory()
  }
}
</script>
