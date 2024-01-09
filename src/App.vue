<template>
  <h2>Volume tracker (0 - 20)</h2>
  <h3>current volume {{ volume }}</h3>

  <div>
    <button @click="volume += 2">Increase</button>
    <button @click="volume -= 2">Decrease</button>
  </div>
  <input type="text" v-model="movie" />
  <input type="text" v-model="movieInfo.title" />
  <input type="text" v-model="movieInfo.actor" />

  <div>
    <button @click="movieList = movieList.concat(['Gruz 200'])">
      add film
    </button>
  </div>
  <pre>
   {{ movieInfo }}
  </pre>
</template>

<script>
// import vue_flow_component from "./components/vue_flow_component.vue";

export default {
  name: "App",
  data() {
    return {
      volume: 0,
      movie: "Batman",
      movieInfo: {
        title: "",
        actor: "",
      },
      movieList: ["Batman", "Superman"],
    };
  },
  methods: {},
  computed: {},
  watch: {
    volume(newValue, oldValue) {
      if (newValue > oldValue && newValue > 16) {
        console.log("ebat kopat zvuk menshe sdelay");
      }
    },
    movie: {
      handler(newValue) {
        console.log(newValue);
      },
      immediate: true,
    },
    movieInfo: {
      handler(newValue) {
        console.log(`title - ${newValue.title} actor - ${newValue.actor}`);
      },
      deep: true,
    },
    movieList: {
      handler(newValue) {
        console.log(`Updated list: ${newValue}`);
      },
      // deep: true,
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.test {
  text-decoration: underline;
}

body {
  padding-bottom: 25px;
}

.danger {
  color: red;
}
.promoted {
  font-style: italic;
}
.orange {
  color: orange;
}
h1 {
  font-size: 120px;
}

#app {
  padding: 0 16px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
.underline {
  text-decoration: underline;
}
.promoted {
  font-style: italic;
}
.new {
  color: olivedrab;
}
.sold-out {
  color: red;
}
label {
  font-weight: bold;
  display: flex;
  margin-bottom: 5px;
  flex-direction: column;
  width: 200px;
  align-items: flex-start;
  justify-content: center;
}

input + label {
  font-weight: bold;
  display: inline-flex;
  margin-right: 20px;
}

input[type="text"],
textarea,
select {
  display: block;
  width: 400px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
