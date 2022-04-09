<template>
  <section>
    <welcome-dialog
      :openDialog="openDialog"
      v-if="openDialog"
      @close-dialog="closeDialog"
    ></welcome-dialog>
    <div class="try-button-wrapper">
      <div class="try-button-txt">
        <span class="txt-bolder">Try it free 7 days </span>then $20/mo.
        thereafter
      </div>
    </div>
    <form @submit.prevent="handleSubmit">
      <div
        class="input-control"
        :class="{ 'input-is-invalid': firstNameValidation === 'invalid' }"
      >
        <input
          type="text"
          v-model.trim="form.firstName"
          placeholder="First Name"
        />
        <img src="../assets/images/icon-error.svg" />
        <small
          v-if="firstNameValidation === 'invalid'"
          class="input-validation-feedback"
        >
          First Name cannot be empty.
        </small>
      </div>
      <div
        class="input-control"
        :class="{ 'input-is-invalid': lastNameValidation === 'invalid' }"
      >
        <input
          type="text"
          v-model.trim="form.lastName"
          placeholder="Last Name"
        />
        <img src="../assets/images/icon-error.svg" />
        <small
          v-if="lastNameValidation === 'invalid'"
          class="input-validation-feedback"
        >
          Last Name cannot be empty.
        </small>
      </div>
      <div
        class="input-control"
        :class="{ 'input-is-invalid': emailAddressValidation === 'invalid' }"
      >
        <input
          type="text"
          v-model.trim="form.emailAddress"
          placeholder="Email Address"
        />
        <img src="../assets/images/icon-error.svg" />
        <small
          v-if="emailAddressValidation === 'invalid'"
          class="input-validation-feedback"
        >
          Looks like this is not an email.
        </small>
      </div>
      <div
        class="input-control"
        :class="{ 'input-is-invalid': passwordValidation === 'invalid' }"
      >
        <input
          type="password"
          v-model.trim="form.password"
          placeholder="Password"
        />
        <img src="../assets/images/icon-error.svg" />
        <small
          v-if="passwordValidation === 'invalid'"
          class="input-validation-feedback"
        >
          Password cannot be empty.
        </small>
      </div>
      <button class="submit-button">{{ submitButton.toUpperCase() }}</button>
      <p class="form-footer">
        By clicking the button, you are agreeing to our
        <span>Terms and Services</span>
      </p>
    </form>
  </section>
</template>

<script>
import WelcomeDialog from "./WelcomeDialog.vue";

export default {
  components: {
    WelcomeDialog,
  },
  data() {
    return {
      form: {
        firstName: "",
        lastName: "",
        emailAddress: "",
        password: "",
      },
      submitButton: "Claim your free trial",
      firstNameValidation: "pending",
      lastNameValidation: "pending",
      emailAddressValidation: "pending",
      passwordValidation: "pending",
      openDialog: false,
    };
  },
  methods: {
    handleSubmit() {
      console.log("submit the form");
      const emailChecker = /\S+@\S+\.\S+/;
      if (this.form.firstName === "") {
        this.firstNameValidation = "invalid";
      } else {
        this.firstNameValidation = "valid";
      }
      if (this.form.lastName === "") {
        this.lastNameValidation = "invalid";
      } else {
        this.lastNameValidation = "valid";
      }
      if (this.form.password === "") {
        this.passwordValidation = "invalid";
      } else {
        this.passwordValidation = "valid";
      }
      if (!emailChecker.test(this.form.emailAddress)) {
        this.emailAddressValidation = "invalid";
      } else {
        this.emailAddressValidation = "valid";
      }
      if (
        this.firstNameValidation === "valid" &&
        this.lastNameValidation === "valid" &&
        this.emailAddressValidation === "valid" &&
        this.passwordValidation === "valid"
      ) {
        this.openDialog = true;
        this.form.firstName = "";
        this.form.lastName = "";
        this.form.emailAddress = "";
        this.form.password = "";
      }
    },
    closeDialog() {
      this.openDialog = false;
    },
  },
};
</script>

<style lang="scss" scoped>
section {
  width: 50%;
  @media screen and (max-width: 768px) {
    width: 80%;
    margin-bottom: 5rem;
  }
}

.try-button-wrapper {
  font-size: 0.85rem;
  border: none;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(92, 85, 163);
  color: White;
  border-radius: 0.5rem;
  box-shadow: 0px 10px 3px rgb(0 0 0 / 20%);
  cursor: pointer;
  margin-bottom: 1.25rem;
  @media screen and (max-width: 768px) {
    padding: 2rem;
  }
}

.txt-bolder {
  font-weight: 700;
}

.try-button-txt {
  font-weight: 300;
}

form {
  background-color: #fdfdfd;
  border-radius: 0.5rem;
  padding: 1.75rem;
}

.input-control {
  margin-bottom: 1rem;
  input {
    font-family: inherit;
    width: 100%;
    border: 1px solid #e2e2e3;
    font-size: 1rem;
    font-weight: 400;
    padding: 0.75rem 1.5rem;
    border-radius: 0.25rem;
    &:focus {
      outline: none;
      border: 1px solid rgb(92, 85, 163);
    }
  }
  img {
    display: none;
  }
}

.input-control.input-is-invalid {
  position: relative;
  input {
    border: 2px solid hsl(0, 100%, 74%);
    color: hsl(0, 100%, 74%);
    font-weight: 500;
    font-style: italic;
    &::placeholder {
      color: hsl(0, 100%, 74%);
    }
  }
  .input-validation-feedback {
    color: hsl(0, 100%, 74%);
    text-align: right;
    display: block;
    margin-top: 0.5rem;
    font-style: italic;
  }
  img {
    display: block;
    position: absolute;
    right: 0.5rem;
    top: 35%;
    transform: translateY(-50%);
  }
}

.submit-button {
  background-color: #37cc88;
  border: none;
  cursor: pointer;
  width: 100%;
  border-radius: 0.25rem;
  color: White;
  font-family: inherit;
  padding: 0.75rem;
  font-weight: 600;
  box-shadow: inset 0px -4px 1px #4fb889;
  margin-bottom: 0.75rem;
  transition: opacity 0.5s;
  &:active {
    opacity: 0.5;
  }
}

.form-footer {
  font-family: inherit;
  color: rgba(191, 191, 191);
  font-size: 0.25px;
  text-align: center;
  /* display: flex; */
  /* justify-content: center; */
  /* gap: 0.25rem; */
  span {
    color: hsl(0, 100%, 74%);
    font-weight: 500;
    font-style: italic;
  }
}
</style>
