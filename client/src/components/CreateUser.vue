<template>
<div>
    <h1>Create User</h1>
    <form v-on:submit.prevent = "createUser">
         <p>เลขบัตรประจำตัวประชาชน: <input type="text" v-model="user.code"></p>
        <p>ชื่อ: <input type="text" v-model="user.name"></p>
        <p>นามสกุล: <input type="text" v-model="user.lastname"></p>
        <p>ยศตำแหน่ง: <input type="text" v-model="user.rank"></p>
        <p>email: <input type="text" v-model="user.email"></p>
        <p>Password: <input type="text" v-model="user.password"></p>
        <p><button type="submit">create user</button></p>
    </form>
    <hr>
    <div>
        <p>เลขบัตรประจำตัวประชาชน: {{user.code}}</p>
        <p>ชื่อ: {{user.name}}</p>
        <p>นามสกุล: {{user.lastname}}</p>
        <p>ยศตำแหน่ง: {{user.rank}}</p>
        <p>email: {{user.email}}</p>
        <p>Password: {{user.password}}</p>
        
    </div>
</div>
</template>
<script>
import UsersService from '@/services/UsersService'

export default {
    data(){
        return{
            user:{
                code: '',
                name: '',
                lastname: '',
                rank: '',
                email: '',
                password: '',
                status: 'active'
            }
        }
    },
    methods:{
        async createUser(){
            try{
                await UsersService.post(this.user)
                this.$router.push({
                    name: 'users'
                })
            }catch(error){
                console.log(error)
            }
        }
    }    
}
</script>
<style scoped>


</style>