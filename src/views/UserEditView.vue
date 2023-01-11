<template>
    <div>
      <pre>
          {{ $route.query.page }}
      </pre>

      <button @click="login()">
          Login
      </button>
    </div>
</template>

<script>
export default {
  name: "UserEditView",
  created() {
    console.log(this.$router);
  },
  methods: {
    login() {

      //AJAX Login
      this.$router.push('/about')
      console.log("Chegou");
    }
  }
}
</script>

<style scoped>

</style>