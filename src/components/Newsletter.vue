<template lang="">
  <div class="main-container">
    <div class="signup-form-wrapper">
      <h1>Typeform</h1>
      <form>
        <div class="form-group email-input-wrapper">
          <label for="email-input">email</label>
          <input
            @change="checkMail"
            type="text"
            id="email-input"
            placeholder="bruce@wayne.com"
          />
          <p><span id="email-error"> </span></p>
        </div>
        <div class="form-group pwd-input-wrapper">
          <label for="pwd-input">password</label>
          <input
            @change="checkPwd"
            type="password"
            id="pwd-input"
            placeholder="password"
          />
          <p><span id="pwd-error"> </span></p>
        </div>
        <div class="form-group terms-input-wrapper">
          <input @change="checkTerms" type="checkbox" name="terms" id="terms" />
          <label for="terms">accept Terms</label>
        </div>
        <div class="form-group policy-input-wrapper">
          <input @change="checkPolicy" type="checkbox" name="" id="policy" />
          <label for="policy">accept grouop policy</label>
        </div>
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
  </div>
</template>

<script>
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
      policyAccepted
    };
  },
  methods: {
    checkPwd() {
      console.log("checkpwd here");
      let currValue = pwdInput.value;

      if (currValue == "") {
        pwdError.innerText = "";
      } else if (!pwdRegex.test(currValue)) {
        pwdError.innerText = "This password is not valid";
        pwdError.style.color = "rgba(255,0,0,0.4)";
      } else {
        pwdError.innerText = "Nice Password!";
        pwdError.style.color = "rgba(55, 55, 55, 0.3)";
        passwordValid = true;
      }
    },
    checkMail() {
      console.log("checkmnail here");
      if (emailInput.value === "") {
        emailError.innerText = "";
      } else if (emailRegex.test(emailInput.value)) {
        emailError.innerText = "This email seems fine to me";
        emailError.style.color = "rgba(55, 55, 55, 0.3)";
        emailValid = true;
      } else {
        emailError.innerText = "That's not a valid email, dude!";
        emailError.style.color = "rgba(255,0,0,0.4)";
      }
    },
    checkTerms() {
      console.log("checkterms here");
      if (policy.checked) {
        termsAccepted = true;
      }
    },

    checkPolicy() {
      console.log("checkpolicy here");
      if (policy.checked) {
        policyAccepted = true;
      }
    },
    handleSubmit() {
      console.log("handleSubmit here");
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
    console.log("hi everything got mounted");
    console.log(emailInput);
    console.log(this.emailInput);
  }
};
</script>

<style scoped lang="scss">
label {
  display: inline-block;
  width: 100%;
  margin-bottom: 0.5rem;
}

input {
  background-color: #bbb;
  color: #1b1b1b;
}

#pwd-error {
  color: rgba(55, 55, 55, 0.3);
  margin: 0.5rem;
  font-size: 0.8rem;
  display: inline-block;
  min-height: 0.8rem;
}

#email-error {
  color: rgba(55, 55, 55, 0.3);
  margin: 0.5rem;
  font-size: 0.8rem;
  display: inline-block;
  min-height: 0.8rem;
}

.terms-input-wrapper {
  display: flex;
  width: 100%;
  margin-right: auto;
  input[type="checkbox"] {
    flex: 0 0 0%;
  }
  label {
    margin: auto 0 auto 0.5rem;
  }
}

.policy-input-wrapper {
  display: flex;
  justify-content: flex-start;
  width: 100%;
  margin-right: auto;
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
  border: 2px solid gold;
}

.main-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 3rem 0;
  border: 1px solid green;
}

.signup-form-wrapper {
  //   margin-bottom: 5vh;
  width: 100%;
  max-width: 24rem;
  padding: 0.5rem;
  border: 2px solid magenta;
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
    background-color: #333;
    color: #ddd;
    text-decoration: none;
    font-weight: 400;
    border: 2px solid rgb(57, 131, 57);
    border-radius: 8px;
  }
  input:hover {
    cursor: pointer;
  }
}
</style>
