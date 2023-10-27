<template>
  <div class="hello">
    <h1>To do list</h1>
    <form @submit.prevent="addToDo">
      <input type="text" placeholder="Add your work here so it can list (e.g To read a book)" v-model="todo">
    </form>
      <ul>
      <transition-group name="list" enter-active-class="animated rotateInUpLeft" leave-active-class="animated rotateOut">
        <li v-for="(data,index) in todos" :key='index'>{{ data.todo }}
          <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
        </li>
      </transition-group>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data (){
    return{
      todo : '',
      todos : [
        // {'todo' : 'Read a book'}
      ]
    }
  },
  methods :{
    addToDo(){
      this.todos.push({todo : this.todo});
      this.todo = '';
    },
    remove(id){
      this.todos.splice(id,1);
    }
  }
}  
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";
 input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    color : black;
    background-color: #07bebe;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #5bacd8;
    border : 5px solid black;
    margin-bottom: 2px;
    color: black;
  }

  i{
    float : right ;
  }

</style>
