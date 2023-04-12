<template>
  <div class="container">
    <form>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <h1>File a Complaint</h1>
          <hr>
          <div class="form-group">
            <label for="email">Mail</label>
            <input type="text" v-model="userData.email" id="email" class="form-control">
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input type="password" v-model="userData.password" id="password" class="form-control">
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input v-model="userData.age" type="number" id="age" class="form-control">
          </div>

        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <label for="message">Message</label><br>
          <!-- Interpolation between <textarea>{{ test }}</tex  tarea> doesn't work!-->
          <textarea id="message" v-model="message" rows="5" class="form-control"></textarea>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <div class="form-group">
            <label for="sendmail">
              <input type="checkbox" id="sendmail" v-model="sentMail" value="SendMail"> Send Mail
            </label>
            <label for="sendInfomail">
              <input type="checkbox" id="sendInfomail" v-model="sentMail" value="SendInfoMail"> Send Infomail
            </label>
          </div>

        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <label for="male">
            <input type="radio" v-model="gender" id="male" value="Male"> Male
          </label>
          <label for="female">
            <input type="radio" v-model="gender" id="female" value="Female"> Female
          </label>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
          <label for="priority">Pri ority</label>
          <select v-model="selectedPriority" id="priority" class="form-control"> 
            <option v-for="priority in priorities">{{ priority }}</option>
          </select>
        </div>
      </div>
      <hr>
      <div>
       <appSwitch v-model="dataSwitch"></appSwitch> 
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <button class="btn btn-primary" @click.prevent="submitted()">Submit!
          </button>
        </div>
      </div>
    </form>
    <hr>
    <div class="row" v-if="isSubmitted">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h4>Your Data</h4>
          </div>
          <div class="panel-body">
            <p>Mail:{{ userData.email }}</p>
            <p>Password:{{ userData.password }}</p>
            <p>Age:{{ userData.age }}</p>
            <p>Message:{{ message }} </p>
            <p><strong>Send Mail?</strong></p>
            <ul>
              <li v-for="items in sentMail">{{ items }}</li>
            </ul>

            <p>Gender:{{ gender }}</p>

            <p>Priority:{{ selectedPriority }}</p>
            <p>Switched:{{ dataSwitch }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import switch from './components/switched.vue';
import switched from './components/switched.vue'
export default {
  components: { switched },
  data() {

    return {
      userData: {
        email: '',
        password: '',
        age: 27
      },
      message: 'Hi this is the Pre Populated Message',
      sentMail: [],
      gender: 'Male',
      priorities: ['high', 'medium', 'low'],
      selectedPriority:'High',
      dataSwitch: true,
      isSubmitted:false
    };
  },
  components:{
            appSwitch: switched
        },
methods:{
  submitted(){
    this.isSubmitted=-true
  }
}
}
</script>
 
<style></style>