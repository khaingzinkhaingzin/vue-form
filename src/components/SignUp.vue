<template>
  <form>
    <label for="">Email</label>
    <input type="email" required v-model="email">

    <label for="">Password</label>
    <input type="password" required v-model="password">

    <label for="">Role</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <div>
      <label for="">Skills</label>
      <input type="text" @keyup="addSkill" v-model="skill">
    </div>

    <p>{{ skills }}</p>

    <div>
      <input type="checkbox" v-model="accept">
      <label for="">Accept Terms and condition</label>
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
    }
  },
  methods: {
    addSkill(e) {
      if (e.key === ",") {
        this.skills.push(this.skill);
        this.skill = "";
      }
    }
  }
}
</script>

<style>

</style>