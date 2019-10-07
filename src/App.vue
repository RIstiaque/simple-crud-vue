<template>
  <div id="app">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-8 p-5">
          
          <app-users 
            @addOpened="openAdd($event)" 
            :userNew="userNew"
          >
          </app-users>
          
          <app-add-user 
            v-if="addIsOpen" 
            @userStored="addUser($event)" 
            @addClosed="openAdd($event)" 
          >
          </app-add-user>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Users from './components/Users'
import AddUser from './components/UserAdd'
export default {
  name: 'app',
  data:()=>({
    addIsOpen:false,
    userNew:null
  }),
  components: {
    appUsers: Users,
    appAddUser : AddUser
  },
  methods:{
    openAdd(val){
      this.addIsOpen = val
    },
    addUser(user){
      this.userNew = user
    }
  }
}
</script>
