<script>
export default {
  data() {
    return {
      question: '',
      answer: 'Questions usually contain a question mark. ;-)'
    }
  },
  watch: {
    // whenever question changes, this function will run
    question(newQuestion, oldQuestion) {
      if (newQuestion.indexOf('?') > -1) {
        this.getAnswer()
      }
    }
  },
  methods: {
    async getAnswer() {
      setTimeout(()=>{
       this.answer = 'Thinking...' 
      },2000)
      try {
        const res = await fetch('https://yesno.wtf/api')
        this.answer = (await res.json()).answer
      } catch (error) {
        this.answer = 'Error! Could not reach the API. ' + error
      }
    }
  }
}
</script>

<template>
 <div class="main">
   <h1>
     The Watchers
   </h1>
    <p class="">
    Ask a yes/no question:
    <input v-model="question" />
  </p>
     <p>{{ answer }}</p>
  </div>

</template>
<style>
  body{
    background-color:#013d;
    color:white;
  }
  input{
    background-color:pink;
    border-radius:4px;
    outline:none;
    border:none;
    color:black;
    padding:10px;
    margin: 10px;
  }
  .main{
    display:flex;
    align-items:center;
    flex-direction:column;
    justify-content:center;
    margin-top:60px;
  }
</style>