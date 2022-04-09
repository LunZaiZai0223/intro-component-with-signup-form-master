<template>
  <div class="dialog-backdrop">
    <section>
      <header>Welcome</header>
      <div>Thanks for joining us!</div>
      <button @click="$emit('close-dialog', true)">Close</button>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    openDialog: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.dialog-backdrop {
  background-color: rgba(0, 0, 0, 0.4);
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 15;
}

section {
  background-color: #fdfdfd;
  width: 30%;
  padding: 1.75rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 0.5rem;
  @media screen and (max-width: 768px) {
    width: 80%;
  }
  header {
    font-size: 1.75rem;
    margin-bottom: 1rem;
  }
  div {
    margin-bottom: 1rem;
  }
  button {
    border: none;
    border-radius: 0.5rem;
    padding: 0.5rem;
    color: White;
    font-family: inherit;
    cursor: pointer;
    background-color: rgb(92, 85, 163);
  }
}
</style>
