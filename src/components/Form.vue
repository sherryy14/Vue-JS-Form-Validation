<template>
  <h1>Form</h1>

  <div class="container">
    <ul>
      <li v-for="item in errors" v-bind:key="item">{{ item }} is required</li>
    </ul>
  </div>

  <form>
    <label for="name"><u>Name</u>: </label><br />
    <input type="text" id="name" name="name" v-model="user.name" /><br /><br />

    <label for="email"><u>Email</u>: </label><br />
    <input
      type="email"
      id="email"
      name="email"
      v-model="user.email"
    /><br /><br />

    <label for="password"><u>Password</u>: </label><br />
    <input
      type="password"
      id="password"
      name="password"
      v-model="user.password"
    /><br /><br />

    <label><u>Gender</u>: </label><br />
    <label for="male">Male: </label>
    <input
      type="radio"
      id="male"
      value="Male"
      name="gender"
      v-model="user.gender"
    /><br />
    <label for="female">Female: </label>
    <input
      type="radio"
      id="female"
      value="Female"
      name="gender"
      v-model="user.gender"
    /><br /><br />

    <label for="position"><u>Position</u>: </label><br />
    <select name="position" id="position" v-model="user.position">
      <option selected disabled value="">Select Position</option>
      <option>Full Stack Developer</option>
      <option>App Developer</option>
      <option>Social Media</option>
      <option>Graphics</option>
    </select>
    <br /><br />

    <label><u>Projects</u>: </label><br />
    <label for="crm">CRM: </label>
    <input
      type="checkbox"
      id="crm"
      value="CRM"
      name="project"
      v-model="user.project"
    /><br />
    <label for="ecom">E-commerce Website: </label>
    <input
      type="checkbox"
      id="ecom"
      value="E-commerce Website"
      name="project"
      v-model="user.project"
    /><br />
    <label for="lms">LMS Application: </label>
    <input
      type="checkbox"
      id="lms"
      value="LMS Application"
      name="project"
      v-model="user.project"
    /><br />
    <label for="poster">Poster: </label>
    <input
      type="checkbox"
      id="poster"
      value="Poster"
      name="project"
      v-model="user.project"
    /><br />

    <br />
    <button v-on:click="submit" type="button">Submit</button>
  </form>
</template>


<script>
export default {
  name: "UserForm",
  data() {
    return {
      user: {
        name: "",
        email: "",
        password: "",
        gender: "",
        position: "",
        project: [],
      },
      errors: [],
    };
  },
  methods: {
    submit() {
      this.errors = [];
      for (let item in this.user) {
        if (this.user[item] === "" || this.user[item].length === 0) {
          this.errors.push(item);
        }
      }
      if (this.errors.length == 0) {
        alert("Data Submitted");
      }
      console.log("Data:", this.user);
      console.log("Errors:", this.errors);
    },
  },
};
</script>


<style scoped>
label {
  color: rgb(81, 81, 81);
}
button {
  background-color: burlywood;
  padding: 10px 15px;
  border-radius: 5px;
  border: 1px solid;
}
input,
select {
  border: 1px solid gray;
  padding: 5px 10px;
  border-radius: 5px;
}

.container{
    display: flex;
    justify-content: center;
}
ul {
  list-style: none;
  text-transform: capitalize;
  width: 200px;
}
ul li {
  background-color: red;
  margin: 2px 0;
  color: white;
  padding: 5px 0;
}
</style>