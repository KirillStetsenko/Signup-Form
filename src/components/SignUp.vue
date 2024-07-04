<template>
  <div class="form">
    <h1>Sign Up</h1>
    <div class="email">
      <label>Email</label>
      <input type="email" v-model="form.email" />
    </div>

    <div class="password">
      <label>Password</label>
      <input type="password" v-model="form.password" />
    </div>
    <div class="role">
      <label>Role</label>
      <select v-model="form.role">
        <option value="Developer">Web Developer</option>
        <option value="Designer">Web Design</option>
      </select>
    </div>
    <div class="skills">
      <label>Skills</label>
      <input type="text" v-model="currentSkill" @keydown.enter="addSkill" />
      <div class="skillList">
        <div v-for="skill in form.skills" :key="skill">
          <span class="skill" @click="delSkill(skill)">
            {{ skill }}
          </span>
        </div>
      </div>
    </div>
    <div class="terms">
      <input type="checkbox" name="terms" id="terms" v-model="form.terms" />
      <label for="terms">I agree with terms and rules</label>
    </div>
    <button @click="signUp">Sign up</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentSkill: "",

      form: {
        email: "",
        password: "",
        role: "",
        skills: [],

        terms: false,
      },
    };
  },
  methods: {
    signUp() {
      if (
        this.form.email &&
        this.form.password &&
        this.form.role &&
        this.form.terms
      ) {
        console.log(this.form);
      }
    },
    addSkill() {
      this.form.skills.push(this.currentSkill);
      this.currentSkill = "";
    },
    delSkill(s) {
      this.form.skills = this.form.skills.filter((skill) => skill !== s);
    },
  },
};
</script>

<style scoped>
.form {
  margin: 0 auto;
  width: min-content;
  border: 1px solid #000;
  background: #fff;
  border-radius: 20px;
}

.email,
.password,
.role,
.skills,
.terms,
button {
  margin: 10px;
  padding: 5px;
}

label {
  padding: 5px;
  display: block;
  text-align: left;
  font-size: 20px;
}

input:not(input[type="checkbox"]),
select,
option {
  padding: 5px;
  width: 300px;
  font-size: 16px;
  border: none;
  border-bottom: 1px solid #555;
  background: #fff;
}

.terms {
  display: flex;
  justify-content: space-evenly;
}

.res {
  margin: 50px;
}

.skillList {
  display: flex;
  margin-top: 15px;
}

.skill {
  margin: 5px;
  background: #bbb;
  padding: 5px;
  border-radius: 10px;
}
</style>
