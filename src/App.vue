<template>
  <div className="wrapper">
    <h1>Weather App</h1>
    <p>Check the weather in your city</p>
    <input type="text" placeholder="Enter your city">
    <button>go</button>
  </div>
</template>

<script>
export default {
  components: {
  },

  data() {
  },
  methods: {
  },
}
</script>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: rgba(93, 83, 237, 1);
  padding: 20px;
  text-align: center;
  color: #fff;
}

.wrapper h1 {
  margin-top: 50px;
}

.wrapper p {
  margin-top: 20px;
}

.wrapper input {
  margin-top: 30px;
  background: transparent;
  border: 0;
  outline: none;
  color: #fff;
  font-size: 14px;
  padding: 5px 8px;
}

.wrapper input::placeholder {
  color: #fff;
}

.wrapper input:focus {
  border-bottom: 2px solid #67b7e6;
}

.wrapper button {
  color: #fff;
  background: #67b7e6;
  border-radius: 10px;
  border: none;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
}

.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}

</style>
