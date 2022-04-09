<template>
  <div id="app">
    <div class="container">
      <the-context></the-context>
      <the-form></the-form>
    </div>
    <footer class="info">
      <p class="attribution">
        Challenge by
        <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
          >Frontend Mentor</a
        >. Coded by
        <a href="https://github.com/LunZaiZai0223" target="_blank"
          >LunZaiZai0223</a
        >.
      </p>
    </footer>
  </div>
</template>

<script>
import TheContext from "./components/TheContext.vue";
import TheForm from "./components/TheForm.vue";

export default {
  name: "App",
  components: {
    TheContext,
    TheForm,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400;1,500;1,600;1,700&display=swap");

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html,
body {
  width: 100%;
  height: 100%;
}

body {
  font-family: Poppins, sans-serif;
  background-image: url("./assets/images/bg-intro-desktop.png");
  @media screen and (max-width: 768px) {
    background-image: url("./assets/images/bg-intro-mobile.png");
  }
  background-color: hsl(0, 100%, 74%);
  display: flex;
  justify-content: center;
  align-items: center;
  @media screen and (max-width: 768px) {
    height: auto;
  }
}

.container {
  /* margin: 0 auto; */
  display: flex;
  gap: 1rem;
  width: 80%;
  margin: 0 auto;
  align-items: center;
  @media (max-width: 768px) {
    flex-direction: column;
    margin: auto;
    width: auto;
    gap: 0px;
  }
}

.info {
  position: fixed;
  bottom: 0;
  width: 100%;
  text-align: center;
  background-color: #fdfdfd;
  font-size: 0.75rem;
}
</style>
