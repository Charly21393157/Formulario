<template>
  <div>
    <h2>Formulario</h2>

    <form @submit.prevent="submitForm">
      <div>
        <label for="nombre">Nombre:</label>
        <input v-model="formData.nombre" type="text" id="nombre" maxlength="18" required />
      </div>

      <div>
        <label for="apellido">Apellido:</label>
        <input
          v-model="formData.apellido"
          type="text"
          id="apellido"
          maxlength="18"
          :pattern="`^(?!${formData.nombre}$).*$`"
          required
        />
      </div>

      <div>
        <label for="edad">Edad:</label>
        <input v-model.number="formData.edad" type="number" id="edad" min="0" max="60" required />
      </div>

      <div>
        <label for="genero">Género:</label>
        <select v-model="formData.genero" id="genero" required>
          <option value="H">Hombre</option>
          <option value="M">Mujer</option>
        </select>
      </div>

      <div>
        <label for="numeroCelular">Número Celular:</label>
        <input
          v-model.number="formData.numeroCelular"
          type="tel"
          id="numeroCelular"
          maxlength="10"
          required
        />
      </div>

      <button type="submit">Enviar</button>
    </form>

    <div v-if="formSubmitted">
      <h3>Formulario Enviado:</h3>
      <p>Nombre: {{ formData.nombre }}</p>
      <p>Apellido: {{ formData.apellido }}</p>
      <p>Edad: {{ formData.edad }}</p>
      <p>Género: {{ formData.genero }}</p>
      <p>Número Celular: {{ formData.numeroCelular }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  nombre: '',
  apellido: '',
  edad: 0,
  genero: 'H',
  numeroCelular: 0
})

const formSubmitted = ref(false)

const submitForm = () => {
  formSubmitted.value = true
}
</script>

<style>
form {
  display: grid;
  gap: 10px;
  max-width: 400px;
  margin: 0 auto;
}

label {
  font-weight: bold;
}

input,
select {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
}

button {
  padding: 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

div {
  margin-bottom: 15px;
}

h3 {
  color: #4caf50;
}
</style>
