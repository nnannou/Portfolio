<template>
    <section id="formulaire">
      <h2>Formulaire de contact</h2>
      <div class="container">
        <figure>
          <img src="@/assets/images/sendEmail.png" alt="image envoie d'email">
        </figure>
        <div class="sous-container">
          <label for="Name">Nom & Prénom: </label>
          <input type="text" id="Name" placeholder="John Doe" v-model="name">
          <label for="Email">Email: </label>
          <input type="text" id="Email" placeholder="Email" v-model="email">
          <label for="Object">Objet: </label>
          <input type="text" id="Object" placeholder="Objet" v-model="object">
          <label for="message">Message: </label>
          <textarea id="message" placeholder="Message" v-model="message"></textarea>
            <button type="button" value="Envoyer" id="send" @click="sendEmail">Envoyer</button>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  // Propriétés réactives pour suivre les valeurs des champs du formulaire
  const name = ref('')
  const email = ref('')
  const object = ref('')
  const message = ref('')
  
// Fonction pour envoyer un e-mail avec les données du formulaire
const sendEmail = () => {
  const mailto = 'mailto:villette55@gmail.com'
  const subject = `subject=${encodeURIComponent(object.value)}`
  const body = `body=${encodeURIComponent(`Bonjour,

  Voici le message de ${name.value} :

"${message.value}"

Cordialement,
${name.value} - ${email.value}`)}`
  const fullLink = `${mailto}?${subject}&${body}`
  window.open(fullLink, '_self') // Ouvre un nouvel e-mail dans la même fenêtre
}

  </script>
  
  <style scoped>
  #formulaire {
    display: flex;
    flex-direction: column;
  }
  
  #formulaire h2 {
    display: flex;
    justify-content: center;
  }
  
  #formulaire .container {
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  
  .sous-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .sous-container label {
    margin-bottom: 5px;
  }
  
  .sous-container input {
    max-height: 20px;
    width: 300px;
    height: 100%;
    display: flex;
    flex: 1 1 50%;
    border-radius: 10px;
    box-shadow: 2px 2px 5px 1px cadetblue;
    border: none;
    margin-bottom: 10px;
    font-size: 70%;
  }
  .sous-container textarea {
    max-height: 150px;
    max-width: 400px;
    height: 100%;
    display: flex;
    flex: 1 1 50%;
    border-radius: 10px;
    box-shadow: 2px 2px 5px 1px cadetblue;
    border: none;
  }

  .sous-container button {
    max-height: 20px;
    width: 300px;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1 1 50%;
    border-radius: 10px;
    box-shadow: 2px 2px 5px 1px cadetblue;
    border: none;
    margin-bottom: 10px;
    font-size: 70%;
    text-decoration: none;
    margin-top: 10px;
  }

  </style>