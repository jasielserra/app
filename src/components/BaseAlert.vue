<template>
    <div :class=baseClass>
         <p>{{ text }}</p>
          <button @click="onClick()"> X </button>
     </div>
</template>

<script>
export default {
    props: {
      variant :{
        type: String,
        default: 'danger'
      },
      text: {
        type: String,
        default: 'Sem texto'
      },
    },
    computed:{
        baseClass(){
          return [
              'alert',
              this.variant ? `alert-${this.variant}`:''
          ]
        }

    },
  methods: {
      onClick(){
        this.$emit('close')
        console.log("Clicado")
      }
  }

}
</script>

<style scoped>

.alert {
  display: flex;
  justify-content: space-between;
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