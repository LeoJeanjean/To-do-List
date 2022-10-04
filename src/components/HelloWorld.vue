<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
    <div class="form-outline flex-fill">
        <input type="text" id="form2" class="barre1" v-model="newList" placeholder="Nom de la liste"/>
        <button type="button" class="btn btn-info ms-2" @click="AddList">Créer une nouvelle liste</button>
    </div>
    <li class="componentContainer" v-for="(list, index) in lists" :key="list">
        <Todolist v-bind:listName="list" @remove-list='RemoveList(index)'/>
    </li>
</template>

<script>
import Todolist from './Todolist.vue';
export default {
    name: "HelloWorld",
    props: {
        msg: String
    },
    components: { Todolist },
    methods: {
        AddList() {
            this.lists.push(this.newList);
            this.newList = "";
        },
        RemoveList(listIndex) {
            this.lists.splice(listIndex, 1);
        }
    },
    data: function() {
        return {
            lists: [],
            newList: ""
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.barre1{
  display: block;
  width: 50%;
  padding: 0.375rem 0.75rem;
  margin-left: auto;
  margin-right: auto;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border-radius: 0.375rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
.btn{
  margin-top: 8px;
}
.componentContainer{
  width: 100%;
}
</style>
