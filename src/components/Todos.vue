<template>
  <div class="todos ">
    <h1>Todos</h1>

    <form @submit="submitForm">  

    <input type="text" v-model="text">
    <button @click="submitForm" class="add" type="button">ADD A TASK</button>

    </form>
            
            <ul>
                <li v-for="(todo,index) in todos" :key="index">
                        <input class="toggle" type="checkbox" v-model="todo.completed">
                        <span :class="{completed:todo.completed}">
                            {{todo.text}}
                        </span>
                        <button  @click="deleteTodo(index)" class="delete" type="button">Delete</button>
                </li>
            </ul>
  </div>
</template>



<script>
export default {
  name: 'Todos',
  data(){
      return {
          text:"",
          todos:[
              {
                   text:'Reading Ideology and Ideological State Apparatuses ',
                   completed: false
              },
              {
                   text:'Watching Pierrot le Fou By Jean-Luc Godard',
                   completed: false
              },
              {
                   text:'Learning Vue Js Online ',
                   completed: false
              },
          ]
      }
  },
  props: {
    msg: String
  },
  methods:{
      deleteTodo:function(index){
          this.todos.splice(index, 1);
      },
      submitForm:function(e){
          this.todos.push({
              text:this.text,
              completed:false
          });
          e.preventDefault();
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    ul{
        list-style:none;
        padding:0;
        
    }

    li{
        padding:10px 0;
        border-bottom:1px #ccc solid;
    }

    .completed{
        text-decoration:line-through;
    }

    .delete{
        background-color: #e74c3c;
        border: none;
        font-family: "Barlow Condensed";
        color: white;
    }
    .add{
        background-color: #27ae60;
        border: none;
        font-family: "Barlow Condensed";
        font-weight:700;
        color: white;
        font-size:15px;
        margin-left:10px
    }
 

</style>
