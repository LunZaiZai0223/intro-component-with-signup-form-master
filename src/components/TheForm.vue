<template>
  <section>
    <div class="try-button-wrapper">
      <div class="try-button-txt">
        <span class="txt-bolder">Try it free 7 days </span>then $20/mo.
        thereafter
      </div>
    </div>
    <form>
      <div
        v-for="(item, index) in userInput"
        :key="index"
        class="input-control"
      >
        <input type="text" :placeholder="item.placeholder" />
      </div>
      <button class="submit-button">{{ submitButton.toUpperCase() }}</button>
      <small class="form-footer">
        By clicking the button, you are agreeing to our
        <span>Terms and Services</span>
      </small>
    </form>
  </section>
</template>

<script>
export default {
  data() {
    return {
      userInput: [
        {
          firstName: "",
          placeholder: "First Name",
        },
        {
          lastName: "",
          placeholder: "Last Name",
        },
        {
          email: "",
          placeholder: "Email Address",
        },
        {
          password: "",
          placeholder: "Password",
        },
      ],
      submitButton: "Claim your free trial",
    };
  },
};
</script>

<style lang="scss" scoped>
section {
  width: 50%;
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
}

.form-footer {
  font-family: inherit;
  color: rgba(191, 191, 191);
  font-size: 0.25px;
  text-align: center;
  display: flex;
  justify-content: center;
  gap: 0.25rem;
  span {
    color: hsl(0, 100%, 74%);
    font-weight: 500;
    font-style: italic;
  }
}
</style>
