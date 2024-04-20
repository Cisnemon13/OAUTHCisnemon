<template>
    <div class="login-container">
      <div class="login-box">
        <h1 class="login-title">Login con OAuth</h1>
        <img src="https://pbs.twimg.com/media/D8GGOpnX4AAeIvQ?format=jpg&name=large">
        <div v-if="!$auth.loading" class="button-container">
          <b-button v-if="!$auth.isAuthenticated" @click="login" class="login-button">Iniciar Sesión</b-button>
          <b-button v-if="$auth.isAuthenticated" @click="logout" class="logout-button">Cerrar Sesión</b-button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "Home",
    methods: {
      login() {
        this.$auth.loginWithRedirect();
      },
      logout() {
        this.$auth.logout({
          logoutParams: {
            returnTo: window.location.origin,
          },
        });
      },
    },
  };
  </script>
  
  <style scoped>
  .login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: white;
    margin-left: 30%;
  }
  
  .login-box {
    
    text-align: center;
    padding: 2rem;
    background: white;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    max-width: 320px;
    width: 100%;
  }
  
  .login-title {
    margin-bottom: 2rem;
    color: #333;
  }
  
  .button-container {
    display: flex;
    flex-direction: column;
  }
  
  .login-button {
    background-color: #0056b3;
    color: white;
    border: none;
    margin-bottom: 1rem;
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .logout-button {
    background-color: #dc3545;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
    border-radius: 4px;
    cursor: pointer;
  }

  img{
    height: 70%;
    width: 70%;
  }
  
  .login-button:hover,
  .logout-button:hover {
    opacity: 0.8;
  }
  </style>
  