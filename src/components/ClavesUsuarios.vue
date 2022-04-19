<template>
  <div className="indecision-container">
    <input type="text" @keyup.enter="getAnswer" v-model="question" placeholder="Usuario">
    <div v-if="isValidQuestion" class="tarjeta">
      <h2>{{ question.toLowerCase() }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "ClavesUsuarios",
  data() {
    return {
      question: this.question,
      answer: null,
      isValidQuestion: false,
    }
  },
  methods: {

    async getAnswer() {
      this.isValidQuestion = true;
      this.answer = 'Buscando...';
      const {usuario} = await fetch('http://10.130.161.110:8000/' + this.question.toLowerCase()).then(r => r.json());
      this.answer = usuario;
    },
  },
  watch:{
    question(value, oldValue) {
      if(value.isEmpty || value.length < 1) {
        this.isValidQuestion = false;
        return;
      };
    }
  }
}
</script>

<style scoped>
.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 90vmin;
  padding: 20px 0px;
  border-radius: 5px;
  border: 5px solid rgba(57, 200, 185, 0.40);
  margin: 50px auto;
  font-size: xx-large;
  background-color: rgba(240, 248, 255, 0.30);
  text-align: center;
  box-shadow: rgba(70, 203, 192, 0.40) 17px 19px 20px;
}

input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1, h2 {
  color: white;

}

h1 {
  text-decoration: underline;
  color: #14192b;
}

h2 {
  margin-top: 50px;
}

.tarjeta {
  border: 5px solid rgba(57, 200, 185, 0.40);
  background-color: rgba(240, 248, 255, 0.30);
  color: black;
  box-shadow: rgba(70, 203, 192, 0.40) 17px 19px 20px;

}
</style>
