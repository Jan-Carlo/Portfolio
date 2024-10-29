<template>
  <div class="contact-container fade-zoom-up">
    <h1>Let's get in touch! 👋😎</h1>

    <form @submit.prevent="sendEmail" class="contact-form">
      <div class="form-group">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="form.name" required>
      </div>
      <div class="form-group">
        <label for="message">Message:</label>
        <textarea id="message" v-model="form.message" required></textarea>
      </div>
      <button type="submit" class="btn-submit">Send Email</button>
    </form>

    <h2>Or Contact Me on Facebook Messenger</h2>
    <button @click="openFacebookMessenger" class="btn-facebook">Chat via Facebook Messenger</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        message: ''
      },
      facebookPageId: 'your_facebook_page_id', // Replace with your actual Facebook Page ID
    }
  },
  computed: {
    facebookMessengerLink() {
      return `https://m.me/${this.facebookPageId}`;
    }
  },
  methods: {
    sendEmail() {
      const subject = encodeURIComponent("Portfolio Inquiry from " + this.form.name);
      const body = encodeURIComponent(this.form.message);
      const mailtoLink = `mailto:delacerna.jancarlo@gmail.com?subject=${subject}&body=${body}`;
      window.location.href = mailtoLink;
    },
    openFacebookMessenger() {
      window.open(this.facebookMessengerLink, "https://www.facebook.com/jancarlo.delacerna.5");
    }
  }
}
</script>

<style scoped>
.contact-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  background-color: #1d1d1d;
  border-radius: 20px;
  border: 2px solid transparent;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  color: #ffffff;
  position: relative;
  transition: border 0.3s ease;
  border: 2px solid #add8e6; 
  box-shadow: 0 0 15px #add8e6; 
}

h1, h2 {
  text-align: center;
  color: #f1f1f1;
  margin-bottom: 20px;
}

.contact-form {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}

input[type="text"],
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 20px;
  font-size: 16px;
  background-color: #2d2d2d;
  color: #ffffff;
  transition: border-color 0.3s;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #add8e6;
  box-shadow: 0 0 8px #add8e6;
}

textarea {
  height: auto;
  resize: vertical;
}

.btn-submit {
  padding: 12px 20px;
  background-color: #add8e6; 
  color: #282828; 
  border: none;
  border-radius: 20px;
  font-size: 16px;
  font-weight: bold; 
  cursor: pointer;
  margin-top: 10px;
  margin-bottom: 30px;
  transition: background-color 0.3s;
}

.btn-submit:hover {
  background-color: #8db2c3;
}

.btn-facebook {
  padding: 12px 20px;
  background-color: #4267B2; /* Facebook color */
  color: #ffffff; 
  border: none;
  border-radius: 20px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  display: block;
  margin: 0 auto;
  transition: background-color 0.3s;
}

.btn-facebook:hover {
  background-color: #365899;
}

@keyframes fadeZoomUp {
  0% {
    opacity: 0;
    transform: scale(0.5) translateY(50px);
  }
  100% {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}

.fade-zoom-up {
  animation: fadeZoomUp 1s ease-in-out;
}
</style>
