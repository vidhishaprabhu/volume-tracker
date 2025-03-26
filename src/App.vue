<template>
  <div class="container">
    <h2>Volume Tracker (0-20)</h2>
    <h3 class="volume-text">Current Volume: {{ volume }}</h3>

    <button class="btn increase" @click="increaseVolume">Increase</button>
    <button class="btn decrease" @click="decreaseVolume">Decrease</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      volume: 0
    };
  },
  watch: {
    volume(newValue, oldValue) {
      if (newValue >= 16) {
        alert("Too high volume " + newValue + " may cause ear damage");
        this.volume = 0; // Reset volume to 0
      }
    }
  },
  methods: {
    increaseVolume() {
      if (this.volume < 20) this.volume += 2;
    },
    decreaseVolume() {
      if (this.volume > 0) this.volume -= 2;
    }
  }
};
</script>

<style>
.container {
  text-align: center;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  width: 50%;
  margin: auto;
}

.volume-text {
  font-size: 1.5rem;
  font-weight: bold;
}

.btn {
  padding: 10px 20px;
  margin: 10px;
  font-size: 18px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: 0.3s ease;
}

.increase {
  background-color: #4caf50;
  color: white;
}

.increase:hover {
  background-color: #45a049;
}

.decrease {
  background-color: #f44336;
  color: white;
}

.decrease:hover {
  background-color: #d32f2f;
}
</style>
