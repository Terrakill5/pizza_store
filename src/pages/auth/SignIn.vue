<template>
  <div class="area-flex">
    <div class="area">
      <img
        src="../../../img/logo_principal_editado.jpg"
        alt="logo principal de la pagina"
      />
      <titulo>Bienvenido</titulo>
      <p class="gris_ligero">A las mejores pizzas del pais</p>
      <div class="grupoInput">
        <p>
          <input-animado
            v-model="email"
            :enunciado="'Email'"
            :tipo="'email'"
          ></input-animado>
        </p>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
          <path
            d="M224 256c70.7 0 128-57.31 128-128s-57.3-128-128-128C153.3 0 96 57.31 96 128S153.3 256 224 256zM274.7 304H173.3C77.61 304 0 381.6 0 477.3c0 19.14 15.52 34.67 34.66 34.67h378.7C432.5 512 448 496.5 448 477.3C448 381.6 370.4 304 274.7 304z"
          />
        </svg>
      </div>
      <div class="grupoInput">
        <p>
          <input-animado
            v-model="password"
            :enunciado="'Contraseña'"
            :tipo="'password'"
          ></input-animado>
        </p>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
          <!--! Font Awesome Pro 6.1.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
          <path
            d="M80 192V144C80 64.47 144.5 0 224 0C303.5 0 368 64.47 368 144V192H384C419.3 192 448 220.7 448 256V448C448 483.3 419.3 512 384 512H64C28.65 512 0 483.3 0 448V256C0 220.7 28.65 192 64 192H80zM144 192H304V144C304 99.82 268.2 64 224 64C179.8 64 144 99.82 144 144V192z"
          />
        </svg>
      </div>
      <p v-if="errMsg">{{ errMsg }}</p>
      <p><boton-submit @click="register">Log In</boton-submit></p>
      <button class="boton_invisible" @click="apareceContrasena">
        ¿Olvidaste tu contraseña?
      </button>
      <!-- <p>
      <boton-submit @click="signInWithGoogle">Logearse con Google</boton-submit>
    </p> -->
      <p>
        <boton-submit @click="registrarse">Registrarse</boton-submit>
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import InputAnimado from "../../ui/InputAnimado.vue";
import { useStore } from "../../store/Modal.js";
import { useAuthStore } from "../../store/Auth.js";
import { useRouter } from "vue-router";
import BotonSubmit from "../../ui/BotonSubmit.vue";
import Titulo from "../../ui/Titulo.vue";
const usarAuth = useAuthStore();
const store = useStore();
const router = useRouter();
const email = ref("");
const password = ref("");
const errMsg = ref(); //Mensaje de error
async function register() {
  await usarAuth.logear(email.value, password.value);
  if (usarAuth.permite) {
    router.push("/pizzastore");
  }
  usarAuth.falsoPagina();
}

const registrarse = () => {
  router.push("/register");
};

/* async function signInWithGoogle() {
  await usarAuth.signInWithGoogle();
  if (usarAuth.permite) {
    router.push("/pizzastore");
  }
  usarAuth.falsoPagina();
} */

const apareceContrasena = () => {
  store.cambiarMostrar();
  store.ponerCondicion("contrasena");
  setTimeout(function () {
    store.cambiarMostrar();
  }, 2000);
};
</script>

<style scoped>
div {
  text-align: center;
}

h1 {
  margin-bottom: 10px;
}

input {
  padding: 5px;
}

.gris_ligero {
  color: darkgray;
  margin-top: 5px;
}

.grupoInput {
  margin: 0 auto;
  position: relative;
  padding: 10px;
  overflow: hidden;
  width: 250px;
}

.grupoInput svg {
  position: absolute;
  top: 40px;
  right: calc(50% - 100px);
}

.boton_invisible {
  background: none;
  border: 0;
}

input {
  height: 25px;
}

svg {
  height: 15px;
  width: 15px;
}

.area-flex {
  width: 100%;
  height: 100%;
  padding: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
