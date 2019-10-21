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
                    class="list-group-item d-flex justify-content-between"
                >
                    <span>
                        {{user.name}} ( {{user.email}} )
                    </span>
                    <span class="deleteUser" @click="deleteUser(index)">
                        X
                    </span>
                </li>
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
            if (confirm(`Do you want to delete ${this.users[index]['name']}?`)){
                this.users.splice(index,1)
                alert("Succes Deleted!")
            }
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
            cursor: pointer;
            margin-bottom: 1px!important;
        }
        li:hover{
            border: 1px solid red;
        }
    }
    .deleteUser{
        font-size: 20px;
        color: red;
    }
    .deleteUser:hover{
        font-weight: 700!important;
    }
</style>
