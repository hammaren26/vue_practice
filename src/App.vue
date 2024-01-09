<template>
  <h1>Directives</h1>
  <h2 v-once>{{ name }}</h2>
  <button @click="name = 'batman'">click</button>
  <h2 v-pre>{{ name }}</h2>
  <hr />

  <h1>Computed properties</h1>
  <h2>
    Fullname - {{ computedProperties.firstName }}
    {{ computedProperties.lastName }}
  </h2>

  <button @click="changeFullName">Change fullname</button>

  <h2>Computed fullname - {{ fullName }}</h2>
  <h2>
    Total -
    {{
      computedProperties.items.reduce((total, curr) => {
        return total + curr.price;
      }, 0)
    }}
  </h2>

  <h2>Computed total - {{ getTotal }}</h2>

  <button
    type="button"
    @click="
      computedProperties.items.push({ id: 4, title: 'Keyboard', price: 50 })
    "
  >
    click
  </button>

  <h2>Method Total - {{ getTotalMethod() }}</h2>

  <input type="text" v-model.trim="computedProperties.country" />

  <h2>v-for computed properties</h2>
  <ul>
    <li
      :class="item.price"
      v-for="item in computedProperties.items"
      :key="item.id"
    >
      {{ item.title }} {{ item.price }}
    </li>
  </ul>
  <h2>expensive items</h2>
  <ul>
    <li v-for="item in expensiveItems" :key="item.id">
      {{ item.title }} {{ item.price }}
    </li>
  </ul>
</template>

<script>
// import vue_flow_component from "./components/vue_flow_component.vue";

export default {
  name: "App",
  data() {
    return {
      name: "Slava",
      computedProperties: {
        firstName: "Slava",
        lastName: "Tulaev",
        country: "",
        items: [
          {
            id: 1,
            title: "TV",
            price: 100,
          },
          {
            id: 2,
            title: "Phone",
            price: 200,
          },
          {
            id: 3,
            title: "Laptop",
            price: 300,
          },
        ],
      },
    };
  },
  methods: {
    getTotalMethod() {
      console.log("get total method");
      return this.computedProperties.items.reduce((total, curr) => {
        return total + curr.price;
      }, 0);
    },
    changeFullName() {
      this.fullName = "Vyacheslav Popov";
    },
  },
  computed: {
    fullName: {
      get() {
        return `${this.computedProperties.firstName} ${this.computedProperties.lastName}`;
      },
      set(value) {
        const names = value.split(" ");
        this.computedProperties.firstName = names[0];
        this.computedProperties.lastName = names[1];
      },
    },
    getTotal() {
      console.log("get total computed properties");
      return this.computedProperties.items.reduce((total, curr) => {
        return total + curr.price;
      }, 0);
    },
    expensiveItems() {
      return this.computedProperties.items.filter((item) => item.price > 100);
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
