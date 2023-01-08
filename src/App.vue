<template>
  <div>
    One-way data binding <br>
    Two-way data binding <br>
    v-model -> formulários
  </div>
  <br>
  <br>
  <div>
      <label>Nome</label><br>
      <input v-model="name" type="text">
      <br>
        {{ name }}
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

  <div class="todos-item" v-for="(obj, index) in todos" :key="obj.id">
      <img v-if="obj.imgSrc" :src="obj.imgSrc">

        {{index}} - {{ obj.title }}

  </div>

  </div>

</template>

<script>

export default {
  name: 'App',
  components: {

  },
  data(){
     return {
       colors: ['Yellow','Red','Blue','Green'],
       contract: false,
       newletter: 'Não',
       name : 'Jasiel',
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
    "completed": false,
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
