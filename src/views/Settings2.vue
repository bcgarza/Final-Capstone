<template>

    <body class="color">
          <Header />

          <div id="login">

            <form @submit.prevent="login">

                <h1>Settings</h1>
            
                <div role="alert" v-if="invalidCredentials">Invalid username and password!</div>
                
                <div role="alert" v-if="this.$route.query.registration">hank you for registering, please sign in.</div>
                    
                <div class="container">
                    
                    <form id="second">

                        <h2>User Info</h2>

                        <h3>Username</h3>
                        <input type="text" name="username" placeholder="SkittyCameron_9" v-model="user.username" required autofocus>
                        
                        <h3>Username</h3>
                        <input type="text" name="username" placeholder="9lives" v-model="user.username" required autofocus>
                        
                        <h3>Password</h3>
                        <input type="password" name="password" placeholder="********" v-model="user.password" required>
                        
                        <h3>Confirm Password</h3>
                        <input type="password" name="password" placeholder="********" v-model="user.password" required>
                        
                        <input type="submit" value="Update">
                    </form>
                
                </div>
            
            </form>

          </div>

    </body>

</template>

<script>
import authService from '../services/AuthService';
import Header from '../components/Header.vue'

export default {
  name: "settings2",
  components: {
    Header
  },
  data() {
    return {
      user: {
        username: "",
        password: ""
      },
      invalidCredentials: false
    };
  },
  methods: {
    login() {
      authService
        .login(this.user)
        .then(response => {
          if (response.status == 200) {
            this.$store.commit("SET_AUTH_TOKEN", response.data.token);
            this.$store.commit("SET_USER", response.data.user);
            this.$router.push("/");
          }
        })
        .catch(error => {
          const response = error.response;

          if (response.status === 401) {
            this.invalidCredentials = true;
          }
        });
    }
  }
};

</script>

<style scoped>

.form-input-group {
  margin-bottom: 1rem;
}

label {
  margin-right: 0.5rem;
}

body {
    background-color: #fafafa;
    font-family: Arial, sans-serif;
}


.container {
    margin-top: 50px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#register {
  color: rgb(212, 205, 205);
  font-family: 'Sulphur Point';
  font-size: 18px;
  text-decoration: none;
}

#register:hover {
  color: whitesmoke;
}

#second {
    box-shadow:0px 0px 10px 2px #F84AA7;
    padding: 20px;
    width: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 10px;  
}

input[type="text"], input[type="password"] {
    width: 95%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #dbdbdb;
    border-radius: 3px;
    font-size: 14px;
}

input[type="submit"] {
    background-color: #d83256;
    color: whitesmoke;
    border: none;
    padding: 10px 20px;
    border-radius: 10px;
    font-size: 14px;
    font-family: 'Kodchasan';
    font-weight: 600;
    cursor: pointer;
    margin: 10px;
}

input[type="submit"]:hover {
    background-color: #ff3562;
    color: white;
}

#image{
    max-width: 150px;
    height: auto;
    margin-left: auto;
    margin-right: auto;
}

.color{
  background-color: #1B1B3A;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  align-content: center;
  height: 100vh;
}

.register {
  color: black;
}

h1 {
  font-size: 2.4rem;
  font-family: 'Kodchasan', sans-serif;;
  font-weight: 100;
  color: whitesmoke;
  text-align: center;
  margin-top: 5%;
}

h2 {
  font-size: 2.0rem;
  font-family: 'Kodchasan', sans-serif;;
  font-weight: 100;
  color: whitesmoke;
  text-align: center;
  margin-top: 5%;
}

h3 {
  font-size: 1.0rem;
  font-family: 'Kodchasan', sans-serif;;
  font-weight: 100;
  color: whitesmoke;
  text-align: center;
  margin-top: 5%;
}

</style>