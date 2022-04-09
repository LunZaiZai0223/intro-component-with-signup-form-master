<template>
  <section>
    <h1>{{ title }}</h1>
    <p>{{ text }}</p>
  </section>
</template>

<script>
export default {
  data() {
    return {
      title: "Learn to code by watching others",
      text: "See how experienced developers solve problems in real-time. Watching scripted tutorials is great, but understanding how developers think is invaluable.",
    };
  },
};
</script>

<style lang="scss" scoped>
section {
  width: 50%;
  color: White;
  @media screen and (max-width: 768px) {
    width: 80%;
    text-align: center;
    margin: 5rem 0;
  }
}

h1 {
  font-weight: 700;
  font-size: 2.5rem;
  line-height: 2.5rem;
  margin-bottom: 1.5rem;
}
</style>
