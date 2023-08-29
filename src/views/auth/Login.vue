<template>
  <div class="login">
    <div class="login-box">
      <h2 class="login-title">Inicio de sesión</h2>
      <input type="text" placeholder="Correo">
      <input type="password" placeholder="Contraseña">
      <div class="flat-button">Ingresar</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Login',
  components: {
  }
}
</script>

<style>
  .login-box {
    justify-content: center;
    align-items: center;
    width: 500px;
    color: white;
    display: flex;
    flex-direction: column;
    padding-bottom: 150px;
  }

  input {
    width: 100%;
    height: 35px;
    border-radius: 5px;
    border: none;
    margin-bottom: .75rem;
  }

  input::placeholder {
    padding: 0 10px;
  }

  .login {
    display: flex;
    justify-content: center;
    height: 100%;
  }

  .flat-button {
    display: inline-block;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 35px;
    margin-top: .5rem;
    background-color: #3498db;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    text-align: center;
    text-decoration: none;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  /* Hover effect */
  .flat-button:hover {
    background-color: #2980b9; /* Darker background color on hover */
  }

  .login-title {
    display: flex;
    width: 100%;
    text-align: initial;
  }
</style>
