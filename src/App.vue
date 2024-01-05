<script type="module">
  import axios from "axios"
  import VueSweetalert2 from "vue-sweetalert2";


  export default {
    name: "CreateContact",
    data() {
      return {
        form: {
          first_name: "",
          last_name: "",
          phone_number: "",
        },
      }
    },
    methods: {
      submitForm() {
        axios
          .post("https://chequeandome-prompt-garoo.koyeb.app/contact", this.form, {
            headers: {
              Authorization: "Bearer " + import.meta.env.VITE_MANYCHAT,
              "Content-Type": "application/json",
            },
          })
          .then((response) => {
            console.log(response)
            this.$swal({
              title: "Contacto creado",
              text: "El contacto se ha creado correctamente. Puede dirigirse a Manychat para empezar la conversación.",
              icon: "success",
              confirmButtonText: "Ok",
            })
          })
          .catch((error) => {
            console.log(error)
            this.$swal({
              title: "Error",
              text: "Ha ocurrido un error al crear el contacto. " + error,
              icon: "error",
              confirmButtonText: "Ok",
            })
          })
      },
    }
  }
</script>

<template>
  <header>
    <img class="logo" src="/logo2.png" alt="logo" />
    <h1>Crear contacto</h1>
  </header>

  <main>
    <form v-on:submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Nombre</label>
        <input type="text" id="name" placeholder="Nombre" v-model="form.first_name" />
      </div>
      <div class="form-group">
        <label for="lastname">Apellido</label>
        <input type="text" id="lastname" placeholder="Apellido" v-model="form.last_name"/>
      </div>
      <div class="form-group">
        <label for="phone">Teléfono</label>
        <p class="note">Ingresar el código de área y sin guiones</p>
        <input type="number" id="phone" placeholder="50763581615" v-model="form.phone_number"/>
      </div>
      <button type="submit">Crear contacto</button>
    </form>

  </main>
</template>

<style scoped>
* {
  //border: 1px dashed red;
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

.form-group {
  display: flex;
  flex-direction: column;
  align-items: start;

  width: 100%;
  margin: 0.5rem 0;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

input {
  width: 100%;

  padding: 1rem;
  margin: 0.5rem 0 1rem 0;

  border-radius: 0.5rem;
  outline: none;
  font-size: 16px;
}

label {
  font-size: 1.2rem;
  font-weight: bold;
  margin-left: 0.5rem;
}

.note {
  font-size: 1rem;
  margin-left: 0.5rem;
  font-weight: lighter;
  font-style: italic;
  color: #484848;
}

button {
  width: min(100%, 768px);

  padding: 1rem;
  margin: 1rem 0;

  border-radius: 0.5rem;
  outline: none;
  background-color: #000;
  color: #fff;
  border: none;
  cursor: pointer;

  font-size: 16px;
  font-weight: bold;
}

button:hover {
  background-color: #88fbdc;
  color: #000;
  border: 1px solid #000;
}


@media (max-width: 768px) {
  main {
    padding: 1rem;
  }

  .logo {
    width: 200px;
  }
}
</style>
