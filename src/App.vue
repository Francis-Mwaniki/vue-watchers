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
      },1000)
      setTimeout(()=>{
        this.answer = 'Wait a moment...' 
        },2000)
      setTimeout(()=>{
        this.answer = 'Almost there...' 
        },3000)
        setTimeout(async()=>{
          try {
        const res = await fetch('https://yesno.wtf/api')
        this.answer ="Your answer is -:"+ (await res.json()).answer
      } catch (error) {
        this.answer = 'Error! Could not reach the API. ' + error
      }
          },5000)
    }
  }
}
</script>

<template>
 <div class="main">
   <h1 class="main-2">
     <span>The Watchers</span> <img src="./icons8.png"/>
   </h1>
    <p class="">
    Ask a yes/no question:
    <input v-model="question" />
  </p>
     <p>{{ answer }}</p>
  </div>

</template>
<style>
@import url('https://fonts.googleapis.com/css2?family=Oswald&display=swap');
*{
  font-family: 'Oswald', sans-serif;
  margin:0;
  padding:0;
  box-sizing:border-box;
}
  body{
    background-color:#013d;
    color:white;
  }
  .main-2{
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:40px;
    flex-direction:row;
    margin-bottom:20px;
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