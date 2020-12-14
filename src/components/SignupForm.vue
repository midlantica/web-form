<template>
  <form>

    <label>Email: </label>
    <input type="email" required v-model="email">

    <label>Password: </label>
    <input type="password" required v-model="password">

    <label>Role: </label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <div class="terms">
      <input type="checkbox" required v-model="terms">
      <label>Accept terms & conditions</label>
    </div>

    <div>
      <input type="checkbox" value="shaun" v-model="names">
      <label>Shaun</label>
    </div>
    <div>
      <input type="checkbox" value="fred" v-model="names">
      <label>Fred</label>
    </div>
    <div>
      <input type="checkbox" value="jimmy" v-model="names">
      <label>Jimmy</label>
    </div>
    <div>
      <input type="checkbox" value="liz" v-model="names">
      <label>Liz</label>
    </div>

  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
  <p>Names array: {{ names }}</p>

</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: 'designer',
      terms: false,
      names: []
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
</style>
