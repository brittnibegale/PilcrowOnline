<template>
  <section>
    <ul>
      <li>Twitter</li>
      <li>Facebook</li>
      <li>Instagram</li>
      <li>LinkedIn</li>
    </ul>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
section {
  width: 80%;
  margin-left: 10%;
  padding: 40px 0;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

ul {
  list-style: none;
  padding-left: 0;
}

input {
  width: 100%;
}

@media screen and (min-width: 850px) {
  section {
    padding: 40px !important;
  }
}
</style>