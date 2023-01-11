<template>
    <div :class="[alert, {'alert-success': variant === 'success', 'alert-danger':variant === 'danger' }]">
      Seu formulário foi enviado com sucesso!
    </div>
</template>

<script>
export default {
    props: ['variant']
}
</script>

<style scoped>

.alert {
  padding: 5px;
  border-radius: 6px;
  color: gray;
  background: #ddd;
}

.alert-success {
  background: #42b983;
  color: #fff;
}

.alert-danger {
  background: darkred;
  color: #fff;
}
</style>