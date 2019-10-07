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
          
          <app-alert v-if="error"
            :message="errorMessage">
            </app-alert>
            
          <app-add-user 
            v-if="addIsOpen" 
            @alert="displayAlert($event)" 
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
import Alert from './components/Alert'

export default {
  name: 'app',
  data:()=>({
    addIsOpen:false,
    userNew:null,
    errorMessage:"",
    error:false,
  }),
  components: {
    appUsers: Users,
    appAddUser : AddUser,
    appAlert: Alert
  },
  methods:{
    displayAlert(alert) {
      this.errorMessage = alert.message;
      this.error = alert.show;
    },
    openAdd(val){
      this.addIsOpen = val
    },
    addUser(user){
      this.userNew = user
    },
  }
}
</script>
