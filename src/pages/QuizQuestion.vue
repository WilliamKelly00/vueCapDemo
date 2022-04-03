<template>
    <div id="quiz">
        <div v-if="loading" class="loading">Loading...</div>
        <h1>{{question}}</h1>
        <ul>
            <li v-for="(option, index) in options" :key="option">
                <input type="radio" :id="index" :value="option" v-model="selectedOption">
                <label :for="index">{{option}}</label>
            </li>
        </ul>
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

    },
}
</script>

<style>

</style>