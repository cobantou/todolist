<template>
    <div>
        <!--<header-component/>-->
        <div>this is a todolist demo</div>
        <!--<other-component/>-->
        <form v-on:submit.prevent="addTodo">
            <input v-model="todo" placeholder="todolist" name="todo">
            <button type="submit">submit</button>
        </form>

        <ol >
            <li v-for="todo in todolist">{{todo}}</li>
        </ol>
        <P>{{todo}}</P>
    </div>
</template>
<style>

</style>
<script>
    export default{
        data(){
            return{
                msg:'hello vue',
                todo:"",
                todolist:[]
            }
        },
        methods:{
            addTodo(){
               this.todolist.push(this.todo);
               this.onSubmit();
            },
            onSubmit(){
                fetch('/api/todolist/', {
                  method: 'post',
                  headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json'
                  },
                  body: JSON.stringify({
                       "todo":  this.todo
                   })
                }).then(function(response) {
                      return response.json()
                    }).then(function(json) {
                      console.log('parsed json: ', json)
                    }).catch(function(ex) {
                      console.log('parsing failed: ', ex)
                    });
            }
        }
    }




</script>
