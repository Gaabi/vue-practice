<template>
<div class= "users">
<h1> Users</h1>
<form v-on:submit="addUser">
<input type ="text" v-model ="newUser.name" placeholder="Enter Name">
<br/>
<input type ="text" v-model ="newUser.email" placeholder="Enter Email">
<br/>
<input type ="submit" value ="Submit">
</form>

<ul>
    <li v-for ="item in users">
        <input type="checkbox" class="toggle" v-model="item.contacted">
        <span :class = "{contacted :item.contacted}">
          {{item.name}}:{{item.email}}
          <button v-on:click="deleteUser(item)">X</button>
        </span>
    </li>
</ul>
</div>
</template>

<script>
export default{
    name :'users',
    data(){
     return{
      newUser :{ },
      users:[]
    }
},
    methods :{
        addUser :function(e){
            this.users.push({
             name:this.newUser.name,
             email:this.newUser.email,
             contacted:false
            });
            e.preventDefault();
 
        },
        deleteUser:function(item){
            this.users.splice(this.users.indexOf(item),1);
        }
     },
     created :function(){
         this.$http.get('http://jsonplaceholder.typicode.com/users')
         .then(function(response){
             this.users=response.data;

         });
     }

    }
 

</script>

<style scoped>
     .contacted{
    text-decoration:line-through;
   }


   
</style>