<template>
  <header class="header">
     Header for My Home Page
  </header>
</template>

<script>
export default {
  name: 'TheHeader',
  mounted() {
    window.addEventListener('resize',this.resize)
  },
  beforeUnmount() {
    console.log('beforeUnmount');
    window.removeEventListener('resize',this.resize);

  },
  unmounted() {
    console.log('unmounted');
  },
  method: {
    resize($evt){
      console.log($evt);
    }
  }
}
</script>

<style scoped>
    .header {
      background: #000;
      color: #fff;
    }
</style>