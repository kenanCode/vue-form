<template>
  <form @submit.prevent="Submitting"> 
    <label> Email: </label>
    <input type="email" required v-model="email">

    <label> Password: </label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error"> {{ passwordError }}</div>
    
    <label> Role: </label>
    <select v-model="role">
      
      <option value="Frontend Engineer"> Frontend Developer </option>
      <option value="Backend Developer"> Backend Developer </option>
      <option value="Fullstack Developer"> Fullstack Developer </option>
      <option value="DevOps Developer"> DevOps Developer </option>
      <option value="Mobile Developer"> Mobile Developer </option>
      <option value="Game Developer"> Game Developer </option>
      <option value="Web Designer"> Web Designer </option>
      <option value="Software Engineer"> Software Engineer </option>
      <option value="Machine Learning Engineer"> Machine Learning Engineer </option>
      <option value="Product Manager"> Product Manager </option>
      <option value="Data Scientist"> Data Scientist </option>
      <option value="Developer Relations"> Developer Relations </option>

    </select>

    <label> Skills: </label>
    <input type="text" v-model="enterSkill" @keyup.alt="yourSkill">
    <div v-for="skill in skills" :key="skill" class="skillStyle" >
   <span @click="deleteSkill(skill)"> {{  skill }} </span>
    </div>

    <div class="terms">
     <input type="checkbox" required v-model="terms">
     <label> Accept terms and conditions* </label>
    </div>
    <div>
      <input type="checkbox" value="updates" v-model="conditions">
      <label> Receive our weekly updates </label> 
    </div>
    <div>
      <input type="checkbox" value="newsletter" v-model="conditions">
      <label> Receive our monthly newsletter </label> 
    </div>
    <div>
      <input type="checkbox" value="prices" v-model="conditions">
      <label> Receive special offers for new subscriptions </label> 
    </div>

    <div class="submit">
    <button> Create Account </button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: '',
      terms: false,
      conditions: [],
      enterSkill: '',
      skills: [],
      passwordError: ''
    }
  },
  methods: {
   yourSkill(e) {
    if(e.key === ',' && this.enterSkill) {
      if (!this.skills.includes(this.enterSkill)) {
      this.skills.push(this.enterSkill)
      }
      this.enterSkill = ''
    }
   },
   deleteSkill(skill){
    this.skills = this.skills.filter((item => {
     return skill !== item
    }))
   },
   Submitting() {
  this.passwordError = this.password.length > 7 ? '' : 'Password must be at least 7 characters long'
  
  if(!this.passwordError) {
    console.log('email: ', this.email)
    console.log('password: ', this.password)
    console.log ('role: ', this.role)
    console.log('skills: ', this.skills)
    console.log('terms accepted: ', this.terms)
    console.log('conditions: ', this.conditions)
    }
   }
  }
}
</script>

<style>
form {
max-width: 420px;
margin: 30px auto;
background: white;
border-radius: 10px;
padding: 40px;
text-align: left;
}

label {
  color: rgb(72, 72, 101);
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.7em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input, select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid greenyellow;
  color: rgb(223, 160, 160)
}

input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}

.skillStyle {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 7px 13px;
  background: blueviolet;
  border-radius: 30px;
  font-size: 13px;
  letter-spacing: 1px;
  font-weight: bold;
  cursor: pointer;
}


button {
  background: blue;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
  cursor: pointer;
}

.submit {
  text-align: center;
}

.error {
  color: red;
  margin-top: 10px;
  font-size: 0.7em;
  font-weight: bold;
}
</style>