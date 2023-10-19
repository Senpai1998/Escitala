<script setup>
  
  import { defineProps, ref } from 'vue';
  import {encryptMessage, decryptMessage} from './MetodoSJCL'
  
  const message = ref(''); 
  const encryptedMessage = ref(''); 
  const decryptedMessage = ref(''); 
  
  defineProps({
    msg: String,
  })
  
  const encryptMessageHandler = () => {
    encryptedMessage.value = encryptMessage(message.value, 'tu-contrasena');
  };

  const decryptMessageHandler = () => {
    decryptedMessage.value = decryptMessage(encryptedMessage.value, 'tu-contrasena');
  };
  
</script>

<template>
  <div class="container">
    <h1 class="text-center">{{ msg }}</h1>
    <div class="mb-3">
      <label for="message" class="form-label">Mensaje:</label>
      <input type="text" v-model="message" id="message" class="form-control">
    </div>
    <button @click="encryptMessageHandler" class="btn btn-primary">Encriptar</button>
    <button @click="decryptMessageHandler" class="btn btn-secondary">Desencriptar</button>

    <div class="mt-3">
      <p>Mensaje Encriptado: {{ encryptedMessage }}</p>
      <p>Mensaje Desencriptado: {{ decryptedMessage }}</p>
    </div>
  </div>
</template>