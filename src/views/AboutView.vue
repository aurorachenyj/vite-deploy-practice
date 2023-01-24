<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ userData }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: {},
    };
  },
  mounted() {
    console.log(import.meta.env.VITE_text);
    console.log(import.meta.env.VITE_Path);
    this.$http
      .get(`https://randomuser.me/api/`)
      .then((res) => {
        console.log(res.data);
        this.userData = res.data.results[0];
        console.log(this.userData);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
