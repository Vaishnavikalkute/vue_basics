<template>
<div>
    <button @click="getPosts">load data</button>
    <h3 v-if="errormsg">{{ errormsg }}</h3>
    <div v-for="post in posts" :key='post.id'>
        <h3>{{post.id }}.{{post.task}}</h3>

    </div>
</div>
</template>

<script>
import axios from 'axios'
export default{
    name:'post_list',
    data(){
        return{
            posts:[],
            errormsg:'',
        }
    },
    methods:{
        getPosts(){
            // axios.get('https://jsonplaceholder.typicode.com/posts')
            axios.get('http://127.0.0.1:8000/todo')
            .then((response)=>{
                console.log(response.data)
                this.posts=response.data
            })
            .catch((error)=>{
                console.log(error)
                this.errormsg='Error while retriving data'
            }
            )
        }
    }
}

</script>

<style scoped>

</style>