<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- <div class="form-container"> -->
    <SignInForm
      :email="email"
      :password="password"
      @handleFormChange="handleFormChange"
      @handleSubmit="handleSubmit"
    />
    <!-- <form @submit="handleSubmit">
        <input
          placeholder="Email"
          :value="email"
          name="email"
          type="email"
          v-on:input="handleFormChange"
        />
        <input
          placeholder="Password"
          :value="password"
          name="password"
          type="password"
          @input="handleFormChange"
        />
        <button>Log In</button>
      </form> -->
    <!-- </div> -->
  </div>
</template>

<script>
import "./styles/app.css";
import SignInForm from "./components/SignInForm.vue";
export default {
  name: "App",
  components: {
    SignInForm,
  },
  data: () => ({
    email: "",
    password: "",
  }),
  methods: {
    // handleFormChange(e) {
    //   this[e.target.name] = e.target.value;
    // },
    // handleSubmit(e) {
    //   e.preventDefault();
    //   alert("Form Submitted");
    //   this.email = "";
    //   this.password = "";
    // },
    handleFormChange(name, value) {
      this[name] = value;
    },
    handleSubmit() {
      alert("Form Submitted");
      (this.email = ""), (this.password = "");
    },
  },
};
</script>
