<template>
  <div>
    <div class="container">
      <div class="row-play">
        <button class="btn btn-play" @click="play()">Play</button>
      </div>

      <div class="row-input">
        <input v-model="input" placeholder="Choose a number 0~9">
        <button class="btn btn-confirm" @click="verify()" :disabled="answered">Confirm</button>
      </div>

      <div class="row-next">
        <button class="btn btn-next" @click="next()">Next</button>
      </div>
    </div>

    <div class="container">
      <div v-if="answered && isAnswerCorrect" class="message">Awesome ear! :)</div>
      <div v-if="answered && !isAnswerCorrect" class="message">
        <div v-if="answered && !isAnswerCorrect" class="message">You're wrong :(</div>
        <button class="btn btn-answer" @click="viewAnswer()">What is it?</button>
        <div v-if="showAnswer" class="answer">Correct answer: {{ correctNumber }}</div>
      </div>
    </div>

    <div class="score">Your score: {{ correct }}/{{ total }}</div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      input: '',
      correctNumber: 0,
      showAnswer: false,
      correct: 0,
      total: 0,
      answered: false
    }
  },

  computed: {
    isAnswerCorrect () {
      return this.input === this.correctNumber.toString()
    }
  },

  watch: {
    total () {
      console.log('Load and playing...')

      this.correctNumber = Math.floor(Math.random() * 10)

      this.resetAll()
    }
  },

  mounted () {
    this.total++
  },

  methods: {
    next () {
      console.log('Switch to next...')

      this.total++
    },
    play () {
      console.log('Playing...')
    },
    verify () {
      if (!this.answered && this.correct < this.total) {
        if (this.isAnswerCorrect) {
          this.correct++
        }
      }

      this.answered = true
    },
    viewAnswer () {
      this.showAnswer = true
    },
    resetAll () {
      this.input = ''
      this.answered = false
      this.showAnswer = false
    }
  }
}
</script>

<style scoped>
.container {
  width: 250px;
  margin: auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.row-play {
  align-self: flex-start;
}

.row-input {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.row-next {
  align-self: flex-start;
}

.message {
  margin-top: 10px;
}

.btn-answer {
  margin-top: 10px;
}

.score {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 50px;
}
</style>
