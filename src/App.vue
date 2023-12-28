<template>
  <h1>Methods</h1>
  <h2>{{ 2 + 3 + 5 }}</h2>
  <h2>Add method - {{ add(1, 2, 3) }}</h2>
  <h2>{{ multiply() }}</h2>
  <hr />
  <br />
  <br />
  <br />

  <h1>Events</h1>
  <h2>{{ name }}</h2>
  <button @click="changeName('Superman', $event), increment()">
    Change name
  </button>
  <br />
  <h2>count: {{ count }}</h2>
  <button @click="increment">Icrement</button>
  <button @click="decrement">Decrement</button>
  <hr />
  <br />
  <br />
  <br />

  <h1>Form Handling</h1>
  <pre>
   {{ JSON.stringify(formValues, null, 2) }}
  </pre>
  <form>
    <div>
      <label>
        <div>Name:</div>
        <input
          style="display: block"
          type="text"
          v-model="formValues.name"
          required
        />
      </label>
      <label>
        <div>Profile Summary</div>
        <textarea v-model="formValues.profileSummary"> </textarea>
      </label>
      <label>
        <div>Country</div>
        <select name="" id="" v-model="formValues.country">
          <option value="">Select a country</option>
          <option value="India">India</option>
          <option value="China">China</option>
        </select>
      </label>
      <label>
        <div>Job location</div>
        <select multiple name="" id="" v-model="formValues.jobLocation">
          <option value="">Select a country</option>
          <option value="India">India</option>
          <option value="China">China</option>
        </select>
      </label>
      <label>
        <div>Open to remove work</div>
        <input
          style="display: block"
          type="checkbox"
          v-model="formValues.remoteWork"
          true-value="yes"
          false-value="no"
        />
      </label>

      <div>
        <h2>Skill Set</h2>
        <label>
          <span>html</span>
          <input type="checkbox" value="html" v-model="formValues.skillSet" />
        </label>
        <label>
          <span>css</span>
          <input type="checkbox" value="css" v-model="formValues.skillSet" />
        </label>
        <label>
          <span>js</span>
          <input type="checkbox" value="js" v-model="formValues.skillSet" />
        </label>
      </div>

      <div>
        <h2>Years of Experience</h2>
        <label>
          <span>0-2</span>
          <input
            type="radio"
            value="0-2"
            v-model="formValues.yearsOfExperience"
          />
        </label>
        <label>
          <span>3-5</span>
          <input
            type="radio"
            value="3-5"
            v-model="formValues.yearsOfExperience"
          />
        </label>
        <label>
          <span>6-10</span>
          <input
            type="radio"
            value="6-10"
            v-model="formValues.yearsOfExperience"
          />
        </label>
      </div>
    </div>
    <button>submit</button>
  </form>
</template>

<script>
// import vue_flow_component from "./components/vue_flow_component.vue";

export default {
  name: "App",
  data() {
    return {
      baseMultiplier: 5,
      baseValue: 2,
      name: "Slava",
      count: 0,

      formValues: {
        name: "",
        profileSummary: "",
        country: "",
        jobLocation: [],
        remoteWork: "no",
        skillSet: [],
        yearsOfExperience: "",
      },
    };
  },
  methods: {
    changeName(str, event) {
      this.name = str;
      console.log(event);
    },
    add(a, b, c) {
      return a + b + c;
    },
    multiply(num = this.baseValue) {
      return num * this.baseMultiplier;
    },
    increment() {
      this.count++;
    },
    decrement() {
      if (this.count !== 0) {
        this.count--;
      }
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
