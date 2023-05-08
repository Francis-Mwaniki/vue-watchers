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
       this.answer = 'Thinking...' + '🤔'
      },1000)
      setTimeout(()=>{
        this.answer = 'Wait a moment...' + '🤔'
        },2000)
      setTimeout(()=>{
        this.answer = 'Almost there ...' + '🤔' 
        },3000)
        setTimeout(async()=>{
          try {
        const res = await fetch('https://yesno.wtf/api')
        this.answer ="Your answer is -:"+ (await res.json()).answer +"🎉"
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
     <span>The Watchers</span> <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 36 36" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M2.036 12.322a1.012 1.012 0 010-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178z" />
  <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
</svg>

   </h1>
   <p class="ans">{{ answer }}</p>
    <p class="">
    Ask a yes/no question:
    <input v-model="question" placeholder="Enter Quiz.😁" />
  </p>
  <p style="text-align:center;">
    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M11.48 3.499a.562.562 0 011.04 0l2.125 5.111a.563.563 0 00.475.345l5.518.442c.499.04.701.663.321.988l-4.204 3.602a.563.563 0 00-.182.557l1.285 5.385a.562.562 0 01-.84.61l-4.725-2.885a.563.563 0 00-.586 0L6.982 20.54a.562.562 0 01-.84-.61l1.285-5.386a.562.562 0 00-.182-.557l-4.204-3.602a.563.563 0 01.321-.988l5.518-.442a.563.563 0 00.475-.345L11.48 3.5z" />
</svg>

  hint: include a "?"</p>
   
  </div>
  <!-- footer -->
  <div style="text-align:center;margin-top:20px; display:flex; flex-direction: row; align-items:center;
    justify-content:center; margin:auto;">
    <span>😂</span><span>😂</span><span>😂</span><span>😂</span>
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
  .ans{
   border:1px dashed;
    padding:30px;
    border-radius:2px;
    margin-top:3px;
  }
  .main{
    display:flex;
    align-items:center;
    flex-direction:column;
    justify-content:center;
    margin-top:60px;
  }
</style>