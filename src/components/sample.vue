<template>
  <div class="container" role="main" aria-label="18th Birthday RSVP Invitation" > 
    <div class="sparkle sparkle1"></div>
    <div class="sparkle sparkle2"></div>
    <div class="sparkle sparkle3"></div>
    <div class="sparkle sparkle4"></div>
    <div class="sparkle sparkle5"></div>

    <h1 class="title">You're Invited</h1>
    <h2 class="subtitle">Angela's 18th Birthday Celebration</h2>
    <p class="invitation-text">Join us in celebrating the joy and happiness on ANGELA's special day! We cordially invite you to be a part of a celebration filled with laughter, hugs, and unforgettable moments.</p>

    <form @submit.prevent="handleSubmit" aria-label="RSVP Form">
      <label for="name">Your Name:</label>
      <input type="text" id="name" v-model="name" placeholder="Enter your full name" required autocomplete="off" />

      <label>Will you attend?</label>
      <div class="radio-group" role="radiogroup" aria-labelledby="attendanceLabel">
        <label>
          <input type="radio" v-model="attendance" value="Yes" required /> Yes
        </label>
        <label>
          <input type="radio" v-model="attendance" value="No" /> No
        </label>
      </div>

      <button type="submit" aria-label="Submit RSVP">Submit RSVP</button>
    </form>
    <div v-if="thankYouMessage" class="thankyou-message" role="alert" aria-live="polite">
      {{ thankYouMessage }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      attendance: '',
      thankYouMessage: ''
    };
  },
  methods: {
    handleSubmit() {
      if (!this.name || !this.attendance) {
        alert('Please enter your name and select attendance.');
        return;
      }

      // Display thank you message
      this.thankYouMessage = `Thank you, ${this.name}! Your RSVP that you will ${this.attendance === 'Yes' ? 'attend' : 'not attend'} has been received.`;
      this.name = '';
      this.attendance = '';
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@400;600&display=swap');

/* Reset */
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #ffe6f0 0%, #ffcce3 100%);
  color: #660033;
  min-height: 100vh;
  display: flex;
  /* align-items: center; */
  /* justify-content: center; */
  padding: 2rem;
}

.container {
  background: #fff0f6cc;
  max-width: 450px;
  width: 100%;
  border-radius: 20px;
  box-shadow:
    0 0 15px 5px rgba(255, 192, 203, 0.25),
    0 0 30px 10px rgba(255, 182, 193, 0.3);
  padding: 2.5rem 2rem 3rem 2rem;
  text-align: center;
  /* position: relative; */
  overflow: hidden;

}

/* Diamond sparkle effect shapes */
.sparkle {
  position: absolute;
  width: 16px;
  height: 16px;
  background:
    linear-gradient(45deg, transparent 45%, #fdf8f2 45%, #fdf8f2 55%, transparent 55%),
    linear-gradient(-45deg, transparent 45%, #fdf8f2 45%, #fdf8f2 55%, transparent 55%);
  background-repeat: no-repeat;
  background-position: center;
  background-size: 100% 100%;
  opacity: 0.85;
  animation: sparkle-flicker 3s infinite ease-in-out;
}

@keyframes sparkle-flicker {
  0%, 100% { opacity: 0.85; transform: scale(1) rotate(0deg); }
  50% { opacity: 0.3; transform: scale(1.3) rotate(20deg);}
}

/* Position some sparkles around container */
.sparkle1 { top: 12%; left: 10%; animation-delay: 0s; }
.sparkle
.sparkle2 { top: 30%; right: 15%; animation-delay: 1.2s; }
.sparkle3 { bottom: 25%; left: 25%; animation-delay: 0.7s; }
.sparkle4 { bottom: 12%; right: 20%; animation-delay: 1.6s; }
.sparkle5 { top: 50%; left: 50%; animation-delay: 2.3s; }

/* .title {
  font-family: 'Great Vibes', cursive;
  
  font-size: 3.6rem;
  color: #e60073;
  margin-bottom: 0;
  letter-spacing: 2px;
  text-shadow: 0 0 8px #ff80bf, 0 0 15px #ff3399;
} */
.title {
  font-family: 'Great Vibes', cursive;
  font-size: 3.6rem;
  color: #f5889f;
  margin-bottom: 0;
  letter-spacing: 2px;
  text-shadow: 0 0 8px #eb91a8, 0 0 15px #ff97cb;
}
.subtitle {
  font-weight: 600;
  font-size: 1.25rem;
  margin-top: 6px;
  margin-bottom: 1.8rem;
  color: #cc0066;
}

.invitation-text {
  font-size: 1.1rem;
  margin-bottom: 1.8rem;
  font-style: italic;
  color: #99004d;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}

label {
  font-weight: 600;
  font-size: 1rem;
  color: #660033;
  text-align: left;
}

input[type="text"] {
  padding: 0.8rem 1rem;
  border: 2px solid #ff99cc;
  border-radius: 15px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}
input[type="text"]:focus {
  outline: none;
  border-color: #e60073;
  box-shadow: 0 0 10px #e60073;
}

.radio-group {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
}

.radio-group label {
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
}

input[type="radio"] {
  accent-color: #e60073;
  cursor: pointer;
}

button {
  background: linear-gradient(45deg, #ff66b3, #e60073);
  color:white;
  font-weight: 700;
  font-size: 1.15rem;
  padding: 0.9rem 0;
  border: none;
  border-radius: 25px;
  cursor: pointer;
  box-shadow: 0 0 20px #ff0099aa;
  transition: background 0.3s ease;
}
button:hover {
  background: linear-gradient(45deg, #e60073, #ff66b3);
}
button:focus {
  outline: none;
  box-shadow: 0 0 30px #ff3399;
}

.thankyou-message {
  font-size: 1.3rem;
  font-weight: 600;
  color: #cc0066;
  margin-top: 1.6rem;
  animation: fadeInUp 1s ease forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 500px) {
  .container {
    max-width: 95vw;
    padding: 2rem 1.5rem 2.5rem 1.5rem;
  }
  .title {
    font-size: 2.8rem;
  }
}
</style>
