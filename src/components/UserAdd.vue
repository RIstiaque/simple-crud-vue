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
                    type="email"
                    :class="['form-control', emailState === 'valid' ? 'is-valid' : emailState === 'invalid' ? 'is-invalid' : '']"
                    @input="validateEmail()"
                >
                <div class="invalid-feedback">
                    Enter valid email
                </div>
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
        email:null,
        emailState: null
    }),
    methods:{
        validateEmail() {
            if (
                this.email &&
                this.email.trim().length > 0 &&
                /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(
                    this.email
                )
            ) {
                this.emailState = 'valid'
            } else {
                this.emailState = 'invalid'
            }
        },
        storeUser(){
            this.validateEmail()
            const user = {
                name: this.name,
                email: this.email
            }
            if(user.name != null && this.emailState === 'valid'){
                this.$emit("alert", {message: "", show: false});
                this.$emit('userStored', user)
                this.$emit('addClosed', false)
                this.name=""
                this.email=""
            }else{
                let errorMessage = "Name & Email is required!";
                this.$emit('alert', {message: errorMessage, show: true});
            }
        }
    }
}
</script>
