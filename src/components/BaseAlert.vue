<template>
    <div :class=baseClass>
         <p>{{ text }}</p>
     </div>
</template>

<script>
export default {
    props: ['variant', 'text'],
    computed:{
        baseClass(){
          return [
              'alert',
              this.variant ? `alert-${this.variant}`:''
          ]
        }

    },

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