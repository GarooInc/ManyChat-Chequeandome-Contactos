<script setup>

import CreateContact from "@/components/ContactForm.vue";
</script>

<template>
  <header>
    <img class="logo" src="/logo2.png" alt="logo" />
    <h1>Crear contacto</h1>
  </header>

  <main>
    <CreateContact />
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


@media (max-width: 768px) {
  main {
    padding: 1rem;
  }

  .logo {
    width: 200px;
  }
}
</style>
