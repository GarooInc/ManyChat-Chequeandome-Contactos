<script type="module">
  import axios from "axios"


  export default {
    name: "CreateContact",
    data() {
      return {
        form: {
          first_name: "",
          last_name: "",
          phone: "",
          whatsapp_phone: "",
          email: "",
          gender: "",
          has_opt_in_sms: false,
          has_opt_in_email: false,
          consent_phrase: "Consents",
        },
      }
    },
    methods: {
      submitForm() {
        axios
          .post("http://localhost:8080/fb/subscriber/createSubscriber", this.form, {
            headers: {
              Authorization: "Bearer " + import.meta.env.VITE_MANYCHAT,
            },
          })
          .then((response) => {
            console.log(response)
          })
          .catch((error) => {
            console.log(error)
          })
      },
    }
  }
</script>

<template>
  <header>
    <img class="logo" src="../public/logo2.png" alt="logo" />
    <h1>Crear contacto</h1>
  </header>
  <main>
    <form v-on:submit.prevent="submitForm">
      <input type="text" placeholder="Nombre" v-model="form.first_name" />
      <input type="text" placeholder="Apellido" v-model="form.last_name"/>
      <input type="number" placeholder="Teléfono" v-model="form.whatsapp_phone"/>
      <button type="submit">Crear contacto</button>
    </form>

  </main>
</template>

<style scoped>
* {
  border: 1px dashed red;
}

header {
  display: flex;
  flex-direction: column;
  place-items: center;

  padding: 2rem;
}

header h1 {
  margin: 0;
  padding: 0;
  font-size: 2rem;
  font-weight: bolder;
}

.logo {
  width: 250px;
  margin: 0;
  padding: 0.5rem;
}

main {
  display: flex;
  flex-direction: column;
  place-items: center;
  height: 100%;
  width: 100%;

  padding: 2rem;
}

form {
  display: flex;
  flex-direction: column;
  place-items: center;
  width: 100%;
}

input {
  width: 100%;
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 0.5rem;
  outline: none;
}

button {
  width: 100%;
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 0.5rem;
  outline: none;
  background-color: #000;
  color: #fff;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #88fbdc;
  color: #000;
  border: 1px solid #000;
}


@media (max-width: 768px) {
  header {
  }

  .logo {
    width: 200px;
  }
}
</style>
