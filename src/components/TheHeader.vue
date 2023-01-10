<template>
  <header class="header">

    <h1 v-if="$slots.title" class="title">
     <slot name="title"></slot>
    </h1>

    <div class="description">
      <slot name="description"/>
    </div>

    <div v-if="$slots.content" class="content">
      <slot name="contents"/>
    </div>

  </header>
</template>

<script>
export default {
  name: 'TheHeader',
  mounted() {
    console.log(this.$slots)
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