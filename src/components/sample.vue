<template>
  <div class="container" role="main" aria-label="18th Birthday RSVP Invitation">
    <h1 class="title">You're Invited</h1>
    <br>
    <h2 class="subtitle">To Celebrate Angela’s 18th Birthday</h2>
    <p class="invitation-text">"Join us in celebrating the joy and happiness on ANGELA's special day! We cordially invite you to be a part of a celebration filled with laughter, hugs, and unforgettable moments."</p>

    <form @submit.prevent="handleSubmit" aria-label="RSVP Form">
      <label for="name">Your Name:</label>
      <input @input="findPerson()" type="text" id="name" v-model="name" placeholder="Enter your full name" required autocomplete="off" />

      <label>Will you attend?</label>
      <div class="radio-group" role="radiogroup" aria-labelledby="attendanceLabel">
        <label>
          <input type="radio" v-model="attendance" value="Yes" required /> Yes
        </label>
        <label>
          <input type="radio" v-model="attendance" value="No" /> No
        </label>
      </div>

      <p class="invitation-text">"Bring your enthusiasm and festive spirit! We hope you can make it and celebrate with us."</p>

      <button type="submit" aria-label="Submit RSVP">Submit RSVP</button>
    </form>
    <div v-if="thankYouMessage" class="thankyou-message" role="alert" aria-live="polite">
      {{ thankYouMessage }}
    </div>
    <!-- <button @click="showDialog" class="open-dialog-button">Show Invitation Details</button> -->

    <div v-if="dialogVisible" class="dialog-overlay" role="dialog" aria-labelledby="dialogTitle" aria-describedby="dialogDescription">
      <div class="dialog-content">
        <h2 id="dialogTitle" class="dialog-title">Angela's 18th Birthday Celebration</h2>
        <p id="dialogDescription" class="dialog-description">
          <strong>Date:</strong> [Date of the Party]<br>
          <strong>Time:</strong> [Time of the Party]<br>
          <strong>Venue:</strong> [Venue of the Party]<br>
          <strong>Dress Code:</strong> [Dress Code]
        </p>
        <p class="dialog-additional-info">
            There will be food, music, and lots of fun!  We can't wait to see you there!
        </p>
        <button @click="closeDialog" class="dialog-close-button" aria-label="Close dialog">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      attendance: '',
      thankYouMessage: '',
      attendedD: false,
      eightCandel: [
        { name: 'Ms. Angelica Aquino', value: 'Angelica Aquino' },
        { name: 'Mrs. Marlyn Aquino', value: 'Marlyn Aquino' },
        { name: 'Ms. Louerie Kay Cincua', value: 'Louerie Kay Cincua' },
        { name: 'Ms. Luisa Canales', value: 'Luisa Canales' },
        { name: 'Mrs. Liezel Cincua', value: 'Liezel Cincua' },
        { name: 'Ms. Jenifer Aytona', value: 'Jenifer Aytona' },
        { name: 'Mrs. Clarissa Dionaldo', value: 'Clarissa Dionaldo' },
        { name: 'Ms. Charlmie de Torres', value: 'Charlmie de Torres' },
        { name: 'Mrs. Joan Magno', value: 'Joan Magno' },
        { name: 'Mrs. Jessica Aspiras', value: 'Jessica Aspiras' },
        { name: 'Mrs. Jen-Jen Valdez', value: 'Jen-Jen Valdez' },
        { name: 'Mrs. Floser Nepomuceno', value: 'Floser Nepomuceno' },
        { name: 'Ms. Mila Ansagay', value: 'Mila Ansagay' },
        { name: 'Dra. Weng Catanaoan', value: 'Weng Catanaoan' },
        { name: 'Mrs. Rowena Datinginoo', value: 'Rowena Datinginoo' },
        { name: 'Ms. Ma. Zarah Muli', value: 'Ma. Zarah Muli' },
        { name: 'Mrs. Thelma Muli', value: 'Thelma Muli' },
        { name: 'Mr. Angelo Muli', value: 'Angelo Muli' },
      ],
      dialogVisible: false, // Added for dialog visibility
    };
  },
  methods: {
    handleSubmit() {
      if (!this.name || !this.attendance) {
        alert('Please enter your name and select attendance.');
        this.attendedD = true;
        return;
      }

      // Display thank you message
      this.thankYouMessage = `Thank you, ${this.name}! Your RSVP that you will ${this.attendance === 'Yes' ? 'attend' : 'not attend'} has been received.`;
      this.name = '';
      this.attendance = '';
    },

    findPerson() {
      this.attendedD = true;
      const perso = this.eightCandel.find(r => r.value.toLowerCase() === this.name.toLowerCase());
      if (perso) {
        console.log('Person found:', perso.value);
        this.dialogVisible = true;

      } else {
        console.log('Person not found');
      }
    },
    showDialog() {
      this.dialogVisible = true;
    },
    closeDialog() {
      this.dialogVisible = false;
    },
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
  padding: 2rem;
}

.container {
  background: #ffd2e4cc;
  max-width: 450px;
  width: 100%;
  border-radius: 20px;
  box-shadow:
    0 0 15px 5px rgba(255, 192, 203, 0.25),
    0 0 30px 10px rgba(255, 182, 193, 0.3);
  padding: 2.5rem 2rem 3rem 2rem;
  text-align: center;
  overflow: hidden;

}

.title {
  font-family: 'Great Vibes', cursive;
  font-size: 3.6rem;
  color: #f5889f;
  margin-bottom: 0;
  letter-spacing: 2px;
  text-shadow: 0 0 8px #ffffff, 0 0 15px #ffbaef;
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
  color: white;
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

/* New styles for the dialog */
.open-dialog-button {
  background: linear-gradient(45deg, #a7f3d0, #34d399); /* Tailwind colors, light to dark teal */
  color: #065f46; /* Darker text for contrast */
  font-weight: 600; /* Make the text bold */
  font-size: 1rem;
  padding: 0.75rem 1.5rem; /* Slightly adjusted padding */
  border: none;
  border-radius: 1.5rem; /* More rounded corners */
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2); /* Softer shadow */
  transition: all 0.3s ease; /* Smooth transition for all properties */
  margin-top: 1.5rem;
  display: inline-block; /* Ensure proper spacing */
}

.open-dialog-button:hover {
  background: linear-gradient(45deg, #34d399, #a7f3d0); /* Reverse gradient on hover */
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.3); /* Increased shadow on hover */
  transform: translateY(-2px); /* Slight lift on hover */
}

.open-dialog-button:active {
  transform: translateY(0); /* No lift when active/pressed */
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.2); /* Smaller shadow when active */
}


.dialog-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
  backdrop-filter: blur(4px); /* Add blur to the background */
}

.dialog-content {
  background-color: #ffffff;
  border-radius: 1rem;
  padding: 2rem;
  text-align: center;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3); /* Stronger shadow */
  width: 90%; /* Responsive width */
  max-width: 500px; /* Maximum width */
  animation: fadeIn 0.3s ease; /* Simple fade-in animation */
  transform: translateY(-20px);
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to{
    opacity: 1;
  }
}

.dialog-title {
  font-size: 2rem;
  font-family: 'Great Vibes', cursive;
  color: #f5889f;
  margin-bottom: 1rem;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.dialog-description {
  font-size: 1.1rem;
  color: #6b7280;
  margin-bottom: 1.5rem;
  line-height: 1.6; /* Improved line height for readability */
}
.dialog-additional-info{
    font-size: 1rem;
    color: #660033;
    margin-bottom: 1.5rem;
    font-style: italic;
}

.dialog-close-button {
  background: linear-gradient(to bottom, #f87171, #dc2626); /* Gradient: light red to dark red */
  color: white;
  font-size: 1.1rem;
  font-weight: 600;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 1.5rem; /* Fully rounded corners */
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.4);
}

.dialog-close-button:hover {
  background: linear-gradient(to bottom, #ef4444, #b91c1c); /* Slightly lighter/darker on hover */
  box-shadow: 0 6px 14px rgba(0, 0, 0, 0.4);
  transform: translateY(-2px);
}

.dialog-close-button:active {
  transform: translateY(0);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}


@media (max-width: 500px) {
  .container {
    max-width: 95vw;
    padding: 2rem 1.5rem 2.5rem 1.5rem;
  }
  .title {
    font-size: 2.8rem;
  }
  .dialog-content{
    padding: 1.5rem;
  }
  .dialog-title{
    font-size: 1.75rem;
  }
  .dialog-description{
    font-size: 1rem;
  }
}
</style>
