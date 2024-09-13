<template>
    <!-- Judul-->
     <div class="app-tittle">
    <h1>App Vue</h1>
    </div>

    <!-- Click Counter -->
    <div class="counter-section">
      <h2>Click Counter</h2>
      <button class="styled-button" @click="incrementCounter">
        You clicked me {{ counter }} times
      </button>
    </div>

    <!-- Box Color Changer -->
    <div class="color-changer-section">
      <h2>Box Color Changer</h2>
      <div :style="{ backgroundColor: currentColor }" class="color-box"></div>
      <button class="styled-button" @click="changeColor">Change Color</button>
    </div>

    <!-- Image Carousel -->
    <div class="carousel-section">
      <h2>Image Carousel</h2>
      <div class="carousel">
        <button class="carousel-button" @click="prevImage">⟨</button>
        <img :src="images[currentImage]" class="carousel-image" alt="Image Carousel" />
        <button class="carousel-button" @click="nextImage">⟩</button>
      </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
      colors: ['#FF5733', '#33FF57', '#3357FF', '#FF33F6'],
      currentColor: '#FF5733',
      images: [
        'img/1.jpg',
        'img/2.jpg',
      ],
      currentImage: 0,
    };
  },
  methods: {
    incrementCounter() {
      this.counter++;
    },
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length);
      this.currentColor = this.colors[randomIndex];
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  max-width: 5000px;
  margin: 0 auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  padding: 50px;
  border-radius: 10px;
  background-color: aqua;
}

.app-tittle{
  background: wheat;
  justify-content: center;
  align-items: center;
  color: #333;
  margin: ;
}

h2 {
  color: #333;
  margin-bottom: 20px;
}

.counter-section{
  background-color:darkblue;
  align-items: ;
}
.color-changer-section,
.carousel-section {
  margin-bottom: 50px;
}

.color-box {
  width: 150px;
  height: 150px;
  margin: 20px auto;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: background-color 0.5s ease;
}

.carousel {
  display:flex;
  align-items: center;
  justify-content: center;
}

.carousel-image {
  width: 300px;
  height: 200px;
  border-radius: 10px;
  transition: transform 0.5s ease;
}

.carousel-image:hover {
  transform: scale(1.05);
}

button.styled-button {
  background: linear-gradient(135deg, #ff512f, #f09819);
  border: none;
  color: white;
  padding: 12px 25px;
  font-size: 16px;
  border-radius: 25px;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

button.styled-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(255, 81, 47, 0.3);
}

button.carousel-button {
  background-color: #fff;
  border: 2px solid #ddd;
  color: #333;
  font-size: 24px;
  padding: 5px 15px;
  margin: 0 10px;
  border-radius: 50%;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: background-color 0.3s ease;
}

button.carousel-button:hover {
  background-color: #f0f0f0;
}

button {
  outline: none;
}
</style>
