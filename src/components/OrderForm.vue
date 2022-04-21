<template>
  <v-container>
    <h1>{{ msg }}</h1>

    <ul>
      <li
        v-for="service in services"
        @click="toggleActive(service)"
        v-bind:class="{ active: service.active }"
        :key="service.name"
      >
        {{ service.name }} <br />£{{ service.price }}
      </li>
    </ul>
    <div class="total">Total: {{ total(service) }}</div>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "OrderForm",
  props: {
    msg: String,
  },
  computed: {
    currency(value: number) {
      return "£" + value.toFixed(2);
    },
  },
  data() {
    return {
      services: [
        {
          name: "Web Development",
          price: 299.99,
          active: false,
        },
        {
          name: "Design",
          price: 399.99,
          active: false,
        },
        {
          name: "Integration",
          price: 249.99,
          active: false,
        },
        {
          name: "Training",
          price: 230.49,
          active: false,
        },
      ],
    };
  },
  methods: {
    toggleActive: function (s: { active: boolean }) {
      s.active = !s.active;
    },
    total: function () {
      var total = 0;

      this.services.forEach(function (s) {
        if (s.active) {
          total += s.price;
        }
      });
      return "£" + total;
    },
  },
});
</script>

<style>
[v-cloak] {
  display: none;
}
img {
  width: 200px;
  height: 200px;
}
ul {
  width: 100%;
  align-content: center;
  justify-content: center;
  padding-left: 0;
  display: grid;
}
li {
  background-color: cadetblue;
  color: white;
  border-radius: 4px;
  border-width: 0;
  padding: 10px;
  border: 1px solid white;
  width: 100%;
  margin: 0 auto;
  box-shadow: rgba(45, 35, 66, 0.4) 0 2px 4px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #d6d6e7 0 -3px 0 inset;
  box-sizing: border-box;
  cursor: pointer;
  display: inline-flex;
  font-family: "JetBrains Mono", monospace;
  height: 60px;
  justify-content: center;
  line-height: 1;
  list-style: none;
  overflow: hidden;
  text-align: center;
  text-decoration: none;
  transition: box-shadow 0.15s, transform 0.15s;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: nowrap;
  will-change: box-shadow, transform;
  font-size: 18px;
}

.li:focus {
  box-shadow: #d6d6e7 0 0 0 1.5px inset, rgba(45, 35, 66, 0.4) 0 2px 4px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #d6d6e7 0 -3px 0 inset;
}

.li:hover {
  box-shadow: rgba(45, 35, 66, 0.4) 0 4px 8px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #d6d6e7 0 -3px 0 inset;
  transform: translateY(-2px);
}

.li:active {
  box-shadow: #d6d6e7 0 3px 7px inset;
  transform: translateY(2px);
}
.total {
  height: 40px;
  width: 10%;
  margin: 0 auto;
  box-shadow: rgba(45, 35, 66, 0.4) 0 2px 4px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #d6d6e7 0 -3px 0 inset;
  box-sizing: border-box;
  align-content: center;
  justify-self: center auto;
}
</style>
