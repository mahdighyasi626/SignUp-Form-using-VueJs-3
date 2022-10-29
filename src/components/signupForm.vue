<template>
  <form action="" @submit.prevent="submitHandler">
    <label for="">Email:</label>
    <input type="text" required v-model="email">
    <label for="">Password:</label>
    <input type="password" required v-model="password">
    <div v-if="passwordEra" class="error">{{passwordEra}}</div>
    <label>role</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>
    <label>Skills</label>
    <input type="text" v-model="skillSet" @keyup.alt="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{skill}}</span>
    </div>
    <br>
    
    <input type="checkbox" id="terms" required v-model="terms">
    <label for="terms">Accept Terms and Conditions</label>
 
    <div class="submit">
      <button>Create an Account</button>
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
      skillSet: '',
      skills: [],
      passwordEra: ''
 
    }
  },
  methods: {
    addSkill(e) {
      if (e.key === ',' && this.skillSet) {
        if(!this.skills.includes(this.skillSet)){
              this.skills.push(this.skillSet)
        }
        this.skillSet = ''
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item
      })
    },
    submitHandler() {
      this.passwordEra = this.password.length > 5 ? '' : 'The password should be above 5 characters'
    }
  },
}
</script>

<style>

form { 
max-width: 520px;
margin: 30px auto;
background: white;
/* text-align: center; */
padding: 40px;
border-radius: 10px;
}
label {
color: #aaa;
display: inline-block;
margin: 25px 0 15px;
font-size: 1em;
text-transform: uppercase;
letter-spacing: 1px;
font-weight: bold;
/* float: left; */
}
input, select {
display: block;
padding: 10px 6px;
width: 100%;
box-sizing: border-box;
border: none;
border: 1px solid #ddd;
color: #555;
font-size: 18px;
}
input[type="checkbox"] {
display: inline-block;
width: 16px;
margin: 0 10px 0 0;
position: relative;
top: 2px;
}
.pill {
display: inline-block;
margin: 20px 10px 0 0;
padding: 6px 12px;
background: #eee;
border-radius: 20px;
font-size: 12px;
letter-spacing: 1px;
font-weight: bold;
color: #777;
cursor: pointer;
 }
button {
background: #0b6dff;
border: 0;
padding: 10px 20px;
margin-top: 20px;
color: white;
border-radius: 20px;
 }
 .submit {
  text-align: center;
 }
 .error {
color: #ff0062;
margin-top: 10px;
font-size: 0.8em;
font-weight: bold;
}
</style>