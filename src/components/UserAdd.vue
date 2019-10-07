<template>
    <div class="row mt-5">
        <div class="col-12">
            <h1>Add User</h1>
        </div>
        <div class="col-12">
            <div class="form-group">
                <label for="name">Name</label>
                <input 
                    v-model="name" 
                    type="text" 
                    class="form-control"
                >

            </div>
            <div class="form-group">
                <label for="email">Email</label>
                <input 
                    v-model="email" 
                    type="text" 
                    class="form-control"
                >
            </div>
            <div class="form-group">
                <button 
                    @click="storeUser" 
                    class="btn btn-primary"
                >
                Add</button>

            </div>
        </div>
    </div>
</template>
<script>
export default {
    data:()=>({
        name:null,
        email:null
    }),
    methods:{
        storeUser(){
            const user = {
                name: this.name,
                email: this.email
            }
            if(user.name != null && user.email != null){
                this.$emit('userStored', user)
                this.$emit('addClosed', false)
                this.name=""
                this.email=""
            }else{
                alert("Name & Email is required!")
            }
        }
    }
}
</script>