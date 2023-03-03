<template>
        <div>
        <form @submit.prevent="createcompany">
        <div>
            <label for="Company_Name">User Id</label>
            <input type="text" id="userid" v-model="FormData.company_name">
            <h3>{{ FormData.userid }}</h3>
        </div>
        <!-- <div>
            <label for="password">Password</label>
            <input type="password" id="password" v-model="FormData.password">
        </div> -->

        <button>Create User</button>
    
        </form>
    </div>
    </template>
    
    <script>
    import axios from 'axios'
    export default{
        name:'createcompany',
        data(){
            return{
               FormData:{
                company_name:'',
            
               }
            }
        },
        methods:{
            createcompany(){
                console.log(this.FormData.userid)
                axios.post('http://127.0.0.1:8000/company/',this.FormData)
                .then(response=>
                    console.log(response)
                    
                )
                .catch(error=>
                    console.log(error)
                    
                )
                
            }
        }
    }
    
    </script>
    
    <style scoped>
    
    </style>