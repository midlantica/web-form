<template>
  <form @submit="handleSubmit">

    <label>Email: </label>
    <input type="email" required v-model="email">

    <label>Password: </label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error">{{ passwordError }}</div>

    <label>Role: </label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <div>
      <label>Skills</label>
      <input type="text" v-model="tempSkill" @keyup="addSkill" >
      <div v-for="skill in skills" :key="skill" class="pill">
        <span @click="deleteSkill(skill)">{{ skill }}</span>
      </div>
      <p v-if="mustBeUniqueSkill" class="warning">Must be unique a skill!</p>
    </div>

    <div class="terms">
      <input type="checkbox" required v-model="terms">
      <label>Accept terms & conditions</label>
    </div>

    <div class="submit">
      <button>Create an Account</button>
    </div>

  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
  <p>Skills array: {{ skills }}</p>

</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: 'designer',
      terms: false,
      tempSkill: '',
      skills: [],
      passwordError: '',
      mustBeUniqueSkill: false
    }
  },
  methods: {
    addSkill(e) {
      //console.log(e);
      if(e.key === ',' && this.tempSkill) {
        this.tempSkill = this.tempSkill.slice(0, -1)
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill)
        } else if (this.skills.includes(this.tempSkill)) {
          this.mustBeUniqueSkill = true
        }
        this.tempSkill = ''
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item
      })
    },
    handleSubmit() {
      // validate Password
      this.passwordError = this.password.length > 5 ? '' : 'Password must be at least 6 characters long'
      if(!this.passwordError) {
        console.log('email', this.email);
        console.log('password', this.password);
        console.log('role', this.role);
        console.log('skills', this.skills);
        console.log('terms accepted', this.terms);
      }
      //console.log('form submitted');
    }
  }
}
</script>

<style scoped>
  form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }

  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: .8rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
    text-align: left;
  }

  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    border: 0;
    border-bottom: 1px solid #ddd;
    color: #555;
  }

  select {
    border: 1px solid #ddd;
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
    background: hsl(0deg 0% 83%);
    border-radius: 20px;
    font-size: 12px;
    letter-spacing:1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
    text-transform: uppercase;
  }

  button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 12px;
  }

  .submit {
    text-align: right;
  }
  .error {
    color: red;
    margin-top: 10px;
    font-size: .8rem;
    font-weight: bold;
  }

  .warning {
    color: hsla(0, 100%, 42%, 0.75);
    font-style: italic;
    font-weight: bold;
  }
</style>
