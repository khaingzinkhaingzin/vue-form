<template>
  <form @submit.prevent="submit">
    <label for="">Email</label>
    <input type="email" required v-model="email">

    <label for="">Password</label>
    <input type="password" required v-model="password">
    <p v-if="errorMsg" class="error">{{ errorMsg }}</p>

    <label for="">Role</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <div>
      <label for="">Skills</label>
      <input type="text" @keyup.alt="addSkill" v-model="skill">
    </div>
    <div v-for="skill in skills" :key="skill">
      <p>{{ skill }} <span class="cross" @click="deleteSkill(skill)"> &#x2716;</span></p>
    </div>

    <div>
      <input type="checkbox" v-model="accept">
      <label for="">Accept Terms and condition</label>
    </div>

    <div class="align">
      <button class="create">Create account</button>
    </div>
    
  </form>
  <p>email - {{ email }}</p>
  <p>password - {{ password }}</p>
  <p>role - {{ role }}</p>
  <p>accept - {{ accept }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      accept: false,
      skills: [],
      skill: "",
      errorMsg: "",
    }
  },
  methods: {
    addSkill(e) {
      console.log(e);
      if (e.key === "," && this.skill) {
        this.skills.push(this.skill);
        this.skill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((loopSkill) => {
        return loopSkill !== skill; 
      });
    },
    submit() {
      // validation 
      if (this.password.length < 8) {
        this.errorMsg = "Password must be at least 8 characters.";
      }
    }
  }
}
</script>

<style>
.cross {
  cursor: pointer;
  color: red;
}
.create {
  background-color: royalblue;
  padding: 8px;
  color: white;
  border-radius: 10px;
}
.align {
  text-align: center;
}
.error {
  color: crimson;
}
</style>