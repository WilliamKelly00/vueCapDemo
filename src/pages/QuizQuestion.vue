<template>
    <div id="quiz">
        <div v-if="loading" class="loading">Loading...</div>
        <h1>{{question}}</h1>

        <div v-for="(option, index) in options" :key="option">
          <input type="radio" name="btn" :id="index" :value="option" v-model="chosen"/>
          <label :for="index">{{option}}</label>
        </div>

        <button @click="submit">Submit</button>

    </div>
</template>

<script>
export default {
 data() {
    return {
      loading: false,
      question: null,
      options: null,
      answer: null,
      chosen: null,
    }
  },

  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      this.loading = true
    fetch(`https://opentdb.com/api.php?amount=1&category=18&type=multiple`)
        .then(response => response.json())
        .then(data => {
            this.loading = false;
            this.question = data.results[0].question;
            this.options = data.results[0].incorrect_answers.concat(data.results[0].correct_answer);

            // shuffle the options
            this.options.sort(() => Math.random() - 0.5);

            this.answer = data.results[0].correct_answer;


            console.log(this.question);
            console.log(this.answer);
            
        })
    },
    submit(e) {
        e.preventDefault();
        if (this.chosen === this.answer) {
          alert('Correct!');
        } else {
          alert('Wrong!');
        }

    }
  }
}

</script>

<style>

</style>