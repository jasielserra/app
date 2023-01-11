<template>
  <div>
    <Basealert variant="success"/>
    <TheHeader v-if="showHeader">
      <template v-slot:title>
        Home
      </template>

      <template v-slot:description>
        <p>Dados</p>
      </template>

      <template v-slot:content>
        <p>Conteúdo dos Slots</p>
      </template>

      Content do header - menu ...

    </TheHeader>
    <br><br>
    <button @click="showHeader=!showHeader">
          Ativar e Desativar Header
    </button>
    <br>
    <br>
    <BaseCard/>
    <br>
    <br>
    <div class="card">
       Testando o escopo de uma classe de CSS
    </div>
    <br>
    <button @click="click">Click-me</button>
    <p> {{  fullName }}</p>
  </div>
  <br>
  <br>
  <div>
      <label>Nome</label><br>
      <input v-model="name" type="text">
      <br>
        {{ name }}
      <br><br><br>
      <select v-model="pageCount">
          <option value="5">5</option>
          <option value="10">10</option>
          <option value="15">15</option>
          <option value="20">20</option>
          <option value="25">25</option>
      </select><br><br>
      {{ pageCount }}
      <h1 :class="{ 'title': true, 'title-home': isHome }">Curso VUE 3</h1>
      <label>Sports</label><br>
      <select v-model="sports">
        <option value="">Escolha</option>
        <option value="futebol">Futebol</option>
        <option value="skate">Skate</option>
        <option value="Tenis">Tenis</option>
      </select>
              <br>
              {{ sports }}
    <div>
      <label>Cores que você mais gosta</label><br>
      <input type="checkbox" value="Yellow" v-model="colors"> Yellow
      <input type="checkbox" value="Red" v-model="colors"> Red
      <input type="checkbox" value="Blue" v-model="colors"> Blue
      <input type="checkbox" value="Green" v-model="colors"> Green

      <br>
      <br>
            {{ colors }}

    </div>
  <p :class="pClass">
      Lorem ipsum color sit amet, consectetur adpitgoinh
  </p>

  <p :style="styleClass">
      Esquemas de Cores não deveria Lorem ipsum color sit amet, consectetur adpitgoinh
  </p>
    <h2>Todos em Aberto</h2>
  <div class="todos-item" v-for="(obj, index) in uncompletedTodos" :key="obj.id">
      <!-- <img v-if="obj.imgSrc" :src="obj.imgSrc"> -->

        {{index}} - {{ obj.title }}

  </div>
    <br><br><br>
    <h2>Todos Completadas</h2>
  <div class="todos-item" v-for="(obj, index) in completedTodos" :key="obj.id">
      <!-- <img v-if="obj.imgSrc" :src="obj.imgSrc"> -->

        {{index}} - {{ obj.title }}

  </div>


       <h2>Todos </h2>
  <div class="todos-item" v-for="(obj, index) in todos" :key="obj.id">
      <!-- <img v-if="obj.imgSrc" :src="obj.imgSrc"> -->
  <input v-model="obj.completed" type="checkbox">

        {{index}} - {{ obj.title }}

  </div>

  <div>
     <button @click.once="onClick">
          Enviar
     </button>
     <p @mouseover="onMouseOver"
     @mouseout="onMouseOut"> Mouver Hover</p><br><br>
    <form action="https://www.google.com" @submit.prevent="onSubmit">
      <input type="text" @keyup="onKeyUp">

        <button type="submit"> Enviar </button>
    </form>


  </div>

  </div>

</template>

<script>

import TheHeader from "@/components/TheHeader";
import BaseCard from "@/components/BaseCard";
import Basealert from "@/components/BaseAlert";
export default {
  name: 'App',
  components: {
    Basealert,
    BaseCard,
    TheHeader
  },
//  beforeCreate() {
//    console.log('beforeCreate');
//    console.log('Estado:',this.name);
//    console.log('DOM:',this.$el);
//  },
  // HOOKS
//  create(){
//    console.log('beforeCreate');
//    console.log('Estado:',this.name);
//    console.log('DOM:',this.$el);
//  },
//  beforeMount() {
//    console.log('beforeMount');
//    console.log('Estado:',this.name);
//    console.log('DOM:',this.$el);
//  },
//  mounted() {
//    console.log('mounted');
//    console.log('Estado:',this.name);
//   console.log('DOM:',this.$el);

//  },
//  beforeUnmount() {
//    console.log('beforeUnmount');
//    console.log('Estado:',this.name);
//    console.log('DOM:',this.$el);
//  },
//  unmounted() {
//    console.log('unmouted');
//    console.log('Estado:', this.name);
//    console.log('DOM:',this.$el);
//  },
  methods:{
    click(){
      console.log(this)
    },
    onClick($evt){
      console.log("Click!!", $evt);
    },
    onMouseOver($evt){
      console.log("Moving Mouse Cursor", $evt);
    },
    onMouseOut($evt){
      console.log("Mouse Out!", $evt);
    },
    onSubmit(){
      console.log('Sumit Form');
    },
    onKeyUp($evt){
      console.log('onKeyUp', $evt);
    },
    saveUserName(){
      console.log('Ajax');
      console.log(this.name);
    },
    changePage(){
      console.log('AJAX changePage');
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    },
    uncompletedTodos(){
      return this.todos.filter(todos => !todos.completed);
    },
    completedTodos(){
      return this.todos.filter(todos => todos.completed);
    },

  },
  watch: {
    name(vl){
      if (vl.length >= 3) {
        this.saveUserName()

      }
    },
    pageCount(){
      this.changePage();
    },
    user: {
      handler() {
        console.log("User alterado");

      },
      deep: true
    }
  },
  data(){
     return {
       showHeader: false,
       pageCount: 5,
       colors: ['Yellow','Red','Blue','Green'],
       contract: false,
       newletter: 'Não',
       name : 'Jasiel',
       user : { firstName: 'Jenna', lastName:'Ortega'},
       sports: 'futebol',
       isHome: true,
       classVar: 'title',
       styleClass: {'color': 'aqua', 'backgroundColor':'black', 'font-size': '20px'},
       pClass: ['text', 'text-home'],
       imgAlt:'Foto do meu Avatar',
       todos : [
  {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": true,
    "imgSrc": 'https://via.placeholder.com/150'

  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false,
    "imgSrc": 'https://via.placeholder.com/150'

  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": false
  },
  {
    "userId": 1,
    "id": 4,
    "title": "et porro tempora",
    "completed": true
  },
  {
    "userId": 1,
    "id": 5,
    "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
    "completed": false
  }
]
     }
  }
}
</script>

<style>

.title {
    font-size: 20px;
    color: blue;
}

.title-home {
  font-size: 40px;
  color: greenyellow;
}

.todos-item{
    background: #000;
    margin: 0 0 5px 0;
    padding: 3px 6px ;
    color: #fff
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px;
}
</style>
