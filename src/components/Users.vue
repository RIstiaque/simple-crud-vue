<template>
<div class="row">
    <div class="col-12">
        <h1>List Users</h1>
    </div>
    <div class="col-12">
        <ul class="list-group">

            <li
                v-for="(user,index) in users"
                :key="index"
                @click="deleteUser(index)"
                class="list-group-item"
            >
            {{user.name}} ( {{user.email}} )</li>

        </ul>
    </div>
    <div class="col-12 mt-5">
        <button 
            @click="openAddUser" 
            class="btn btn-primary"
        >
        Add User</button>
    </div>
</div>
</template>
<script>
export default {
    props:['userNew'],
    data:()=>({
        users:[
            {
                name:'Agus Fikri Suyuthi',
                email:'ikrydev@gmail.com'
            },
            {
                name:'Brian',
                email: 'brian@gmail.com'
            }
        ]
    }),
    watch:{
        userNew(){
            this.users.push({
                name: this.userNew.name,
                email: this.userNew.email
            })
        }
    },
    methods:{
        deleteUser(index){
            this.users.splice(index,1)
            alert("Succes Deleted!")
        },
        openAddUser(){
            this.$emit('addOpened', true)
        },
    },
}
</script>
<style lang="scss">
    ul{
        li{
            cursor: pointer
        }
        li:hover{
            background-color: red;
            color: white
        }
    }
</style>
