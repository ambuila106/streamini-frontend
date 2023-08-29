<template>
  <div class="login">
    <div class="login-box">
      <h2 class="login-title">Inicio de sesión</h2>
      <input type="text" placeholder="Correo">
      <input type="password" placeholder="Contraseña">
      <div @click="login()" class="flat-button">Ingresar</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Login',
  components: {
  },

  mounted() {
  },

  methods: {
    login() {
      const formData = {
        grant_type: 'password',
        username: 'admin',
        password: 'admin',
        client_id: 'FH2HatMve040MBZodDD3kJtaMfGJux9AxFfai8DZ',
        client_secret: '2T06uFNcPXx6aeLS4ucCqW91d0W9UPANKhsM03imK8iD0YL1AkputiKMF0IF8mBxFvvcP42UxUjUtLl3OVvaLiWlBZ9007fMkG1sjYG4hRYl4dCKbJKrbGQM4zNaEotd'
      };

      const params = new URLSearchParams(formData);

      fetch('https://localhost:8080/0/token', {
        method: 'POST', // or 'PUT' or 'GET' etc.
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded', // Set the content type
          // You may need to set additional headers as needed
        },
        body: params // Set the encoded data as the request body
      })
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response
      })
      .then(data => {
        console.log(data);
        localStorage.setItem('token', data.access_token00)
      })
      .catch(error => {
        console.error('There was a problem with the fetch operation:', error);
      });

    }
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
