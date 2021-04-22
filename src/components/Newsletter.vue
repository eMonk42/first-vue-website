<template lang="">
  <div class="main-container">
    <img :src="leftImage" alt="here could be your advertisement" />
    <div class="signup-form-wrapper">
      <h1>Subscribe to our Newsletter</h1>
      <form>
        <div class="form-group email-input-wrapper">
          <label for="email-input">Email</label>
          <input
            @change="checkMail"
            type="text"
            id="email-input"
            placeholder="john.smith@fakemail.gov"
          />
          <p><span id="email-error"> </span></p>
        </div>
        <div class="form-group pwd-input-wrapper">
          <label for="pwd-input">Password</label>
          <input
            @change="checkPwd"
            type="password"
            id="pwd-input"
            placeholder="password"
          />
          <p><span id="pwd-error"> </span></p>
        </div>
        <div class="form-group input-wrapper">
          <input @change="checkTerms" type="checkbox" name="terms" id="terms" />
          <label for="terms">accept <a href="">Terms</a></label>
        </div>
        <label class="form-group input-wrapper">
          <input @change="checkPolicy" type="checkbox" name="" id="policy" />
          <label for="policy">accept <a href="">group policy</a></label>
        </label>
        <div class="form-group submit-wrapper">
          <input
            @click.prevent="handleSubmit"
            type="submit"
            value="Submit"
            id="submit-button"
          />
        </div>
      </form>
    </div>
    <img :src="rightImage" alt="here could be your advertisement" />
  </div>
</template>

<script>
import leftImage from "@/assets/images/submit-left.png";
import rightImage from "@/assets/images/submit-right.png";

let emailError = document.getElementById("email-error");
let pwdError = document.getElementById("pwd-error");
let emailInput = document.getElementById("email-input");
let pwdInput = document.getElementById("pwd-input");
let submitForm = document.getElementsByClassName("email-input-wrapper")[0];
let submitButton = document.getElementById("submit-button");
let terms = document.getElementById("terms");
let policy = document.getElementById("policy");

let emailRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

let pwdRegex = /^((?=.*[\d])(?=.*[a-z])(?=.*[A-Z])|(?=.*[a-z])(?=.*[A-Z])(?=.*[^\w\d\s])|(?=.*[\d])(?=.*[A-Z])(?=.*[^\w\d\s])|(?=.*[\d])(?=.*[a-z])(?=.*[^\w\d\s])).{7,30}$/;

let passwordValid = false;
let emailValid = false;
let termsAccepted = false;
let policyAccepted = false;
export default {
  data() {
    return {
      emailError,
      pwdError,
      emailInput,
      pwdInput,
      submitForm,
      submitButton,
      terms,
      policy,
      emailRegex,
      pwdRegex,
      passwordValid,
      emailValid,
      termsAccepted,
      policyAccepted,
      leftImage,
      rightImage
    };
  },
  methods: {
    checkPwd() {
      let currValue = pwdInput.value;

      if (currValue == "") {
        pwdError.innerText = "";
      } else if (!pwdRegex.test(currValue)) {
        pwdError.innerText = "This password is not valid";
        pwdError.style.color = "rgba(255,0,0,0.8)";
      } else {
        pwdError.innerText = "Nice Password!";
        pwdError.style.color = "rgba(55, 55, 55, 0.8)";
        passwordValid = true;
      }
    },
    checkMail() {
      if (emailInput.value === "") {
        emailError.innerText = "";
      } else if (emailRegex.test(emailInput.value)) {
        emailError.innerText = "This email seems fine to me";
        emailError.style.color = "rgba(55, 55, 55, 0.8)";
        emailValid = true;
      } else {
        emailError.innerText = "That's not a valid email, dude!";
        emailError.style.color = "rgba(255,0,0,0.8)";
      }
    },
    checkTerms() {
      if (policy.checked) {
        termsAccepted = true;
      }
    },

    checkPolicy() {
      if (policy.checked) {
        policyAccepted = true;
      }
    },
    handleSubmit() {
      this.checkMail();
      this.checkPolicy();
      this.checkPwd();
      this.checkTerms();
      if (passwordValid && emailValid && policyAccepted && termsAccepted) {
        emailInput.value = "";
        pwdInput.value = "";
        terms.checked = false;
        policy.checked = false;
        alert("you subscribed!");
      } else {
        alert("something is missing...");
      }
    }
  },
  mounted() {
    emailError = document.getElementById("email-error");
    pwdError = document.getElementById("pwd-error");
    emailInput = document.getElementById("email-input");
    pwdInput = document.getElementById("pwd-input");
    submitForm = document.getElementsByClassName("email-input-wrapper")[0];
    submitButton = document.getElementById("submit-button");
    terms = document.getElementById("terms");
    policy = document.getElementById("policy");
  }
};
</script>

<style scoped lang="scss">
label {
  display: inline-block;
  width: 100%;
  margin-bottom: 0.5rem;
  font-weight: 600;
  a {
    text-decoration: none;
    color: #111;
    transition: all 0.3s linear;
    position: relative;
  }
  a::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgb(201, 77, 32);
    transform: scaleX(0);
    height: 1px;
    transform-origin: 0;
    transition: transform 0.2s ease-in-out;
    transition: all 0.2s linear;
  }

  a:hover::after {
    transform: none;
  }
}

input {
  background-color: #bbb;
  color: #1b1b1b;
}

#pwd-error {
  color: rgba(55, 55, 55, 0.3);
  margin: 0.25rem;
  font-size: 0.75rem;
  display: inline-block;
  min-height: 0.75rem;
}

#email-error {
  color: rgba(55, 55, 55, 0.3);
  margin: 0.25rem;
  font-size: 0.75rem;
  display: inline-block;
  min-height: 0.75rem;
}

#email-input {
  padding: 0.5rem;
}

#pwd-input {
  padding: 0.5rem;
}

.input-wrapper {
  display: flex;
  width: 100%;
  margin-right: auto;
  position: relative;
  input[type="checkbox"] {
    flex: 0 0 0%;
  }
  label {
    margin: auto 0 auto 0.5rem;
  }
}

#policy {
  margin-right: auto;
  padding: 0.5rem;
}

.main-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 3px solid rgb(201, 77, 32);
  img {
    max-width: 33%;
  }
}

.signup-form-wrapper {
  //   margin-bottom: 5vh;
  width: 100%;
  max-width: 24rem;
  padding: 1.5rem;
  margin: 1rem;
  border: 1px solid #000;
  box-shadow: 5px 10px #888888;
  background-color: rgba(255, 255, 255, 0.2);
  * {
    width: 100%;
  }
  .submit-wrapper {
    margin: 1rem auto 0 auto;
    max-width: 8rem;
  }
  h1 {
    margin-bottom: 1rem;
    text-align: center;
  }
}

.form-group p {
  min-height: 1rem;
}

.submit-wrapper {
  input {
    background-color: #111;
    color: #ddd;
    text-decoration: none;
    font-weight: 400;
    padding: 0.5rem 0;
    transition: all 0.5s linear;
  }
  input:hover {
    cursor: pointer;
    letter-spacing: 3px;
    background-color: rgb(201, 77, 32);
  }
}

@media (max-width: 1400px) {
  .main-container {
    justify-content: center;
    padding-bottom: 3rem;
    img {
      display: none;
    }
    // .signup-form-wrapper {
    //   max-width: 75%;
    // }
  }
}
</style>
