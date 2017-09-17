<template>
<div class ="test">
    <input type ="text" v-model="title"><br/>
   <h1> {{title}} </h1>
  
   <p v-if="showName">{{user.f_name}}</p>
   <p v-else>Nobody</p>
   <ul>     
   <li v-for="item in arrName">{{item.title}}</li>
   </ul>
   <input type ="text" v-on:keyup="pressKey"><br/>

   <button v-on:click="greet">Click</button>
   <hr/>
   <label>First name</label><input type ="text" v-model="user.f_name">
</br>

<label>Last name</label><input type="text" v-model="user.l_name">
</br>
<p>{{fullName}}</p>
<h3 >{{msg}}</h3>
</div>
</template>

<script>
 export default {
     name:'test',
     props:{
         msg:{
             type:String,
             default: 'default name'
         }
     },
     data(){
         return{
             title:'Hello World',
             user :{
                 f_name: 'Garima',
                 l_name: 'soni'
             },
             showName: true,
             arrName: [
                 {title :'Item one'},
                 {title: 'Item two'},
                 {title : 'Item Three'}
             ]
         }
     },
    methods :{
        greet:function(){
            alert("All the best");
        },
        pressKey:function(){
            console.log("key is pressed");
        }
    },
    computed:{
        fullName :function(){
         return this.user.f_name+ ' '+this.user.l_name
        
        }
    }
 }
 </script>

<style scoped>
</style>