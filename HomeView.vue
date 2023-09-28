<template>
  <div class="weeknd-concert">
    <!-- 1a. Text Interpolation -->
    <h1>The Weeknd's World Tour</h1>

    <h2>Concert Details</h2>
    <!-- 1a. Text Interpolation -->
    <p>Date: {{ concertDate }}</p>
    <!-- 1a. Text Interpolation -->
    <p>Location: {{ concertLocation }}</p>

    <h2>Concert Information</h2>
    <!-- 1b. Raw HTML [v-html] -->
    <p v-html="concertDescription"></p>

    <h2>Buy Tickets</h2>
    <label for="ticketQuantity">Quantity:</label>
    <!-- 8a. v-model with <input type="number"> -->
    <input type="number" v-model="ticketQuantity" />

    <!-- 7a. Event Handling: Listening to Events [v-on:click] -->
    <button @click="buyTickets">Buy Now</button>

    <h2>Featured Songs</h2>
    <ul>
      <!-- 6a. v-for with an Object -->
      <li v-for="song in featuredSongs" :key="song.id">{{ song.title }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const concertDate = 'October 15, 2023';
const concertLocation = 'New York City, NY';
const concertDescription = `
  <p>Join us for an unforgettable night with The Weeknd on his world tour! Experience the magic of his music live.</p>
  <p>Get ready to dance and sing along to your favorite songs.</p>
`;
const ticketQuantity = ref(1);
const featuredSongs = ref([
  { id: 1, title: 'Blinding Lights' },
  { id: 2, title: 'Save Your Tears' },
  { id: 3, title: 'In the Night' },
]);

// 7b. Method Handlers
const buyTickets = () => {
  if (ticketQuantity.value > 0) {
    // Implement ticket purchase logic here
    alert(`You've purchased ${ticketQuantity.value} tickets for The Weeknd's concert!`);
    ticketQuantity.value = 1; // Reset ticket quantity
  }
};
</script>

<style scoped>
.weeknd-concert {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f5f5f5;
  border: 1px solid #ddd;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #333;
  margin-top: 10px;
}

h2 {
  color: #333;
  margin-top: 20px;
}

p {
  margin: 5px 0;
}

button {
  background-color: #f44;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
}

button:hover {
  background-color: #d00;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 5px 0;
}

label {
  display: block;
  margin-top: 10px;
  font-weight: bold;
}

input[type="number"] {
  width: 50px;
  padding: 5px;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 3px;
}
</style>
