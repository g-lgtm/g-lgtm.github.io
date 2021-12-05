<template>
  <div id="contact">
    <div>
      <h1 class="title">Me contacter</h1>
      <div class="container">
        <form @submit.prevent="sendEmail">
          <label>Name</label>
          <input type="text" v-model="name" name="name" placeholder="Your Name">
          <label>Email</label>
          <input type="email" v-model="email" name="email" placeholder="Your Email">
          <label>Message</label>
          <textarea name="message" v-model="message" cols="30" rows="5" placeholder="Message"></textarea>
          <input class="inputspe" type="submit" value="Send">
        </form>
      </div>
    </div>
    <div id="footer">
      <div><strong>Téléphone:</strong> 06 66 60 77 23 </div>
      <div><strong>Email:</strong> gael.leroy@epitech.eu</div>
    </div>
  </div>
</template>

<script>
import emailjs from 'emailjs-com';
export default {
  name: 'Contact',
  data() {
    return {
      name: '',
      email: '',
      message: ''
    }
  },
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm('service_9cwr2r5', 'template_1zkw428', e.target, 'user_2pFxoTG70WAcmaIwP6Kb6', {name: this.name, email: this.email, message: this.message});
      } catch(error) {
        console.log({error});
      }
      console.log(this.message);
      this.name = '';
      this.email = '';
      this.message = '';
    },
  }
}
</script>

<style>

#contact {
  padding-top: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}

* {box-sizing: border-box;}

.container {
  display: block;
  margin:auto;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width: 50%;
}

label {
  float: left;
}

input[type=text], [type=email], textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

.inputspe {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.inputspe:hover {
  background-color: #45a049;
}

.title {
  padding-bottom: 25px;
  font-weight: bolder;
}

#footer {
  color: #000000D7;
  position: absolute;
  bottom: 5px;
  left: 5px;
  right: 5px;
}
</style>