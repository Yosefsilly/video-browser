<template>
  <div>
    <input @input="onInput" placeholder="Search" />
    <button @click="onClick">
      <svg>
        <g>
          <path
            d="M20.87,20.17l-5.59-5.59C16.35,13.35,17,11.75,17,10c0-3.87-3.13-7-7-7s-7,3.13-7,7s3.13,7,7,7c1.75,0,3.35-0.65,4.58-1.71 l5.59,5.59L20.87,20.17z M10,16c-3.31,0-6-2.69-6-6s2.69-6,6-6s6,2.69,6,6S13.31,16,10,16z"
          ></path>
        </g>
      </svg>
    </button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return { query: "" };
  },
  methods: {
    onInput(event) {
      console.log(this.query);

      this.query = event.target.value;
    },
    onClick() {
      console.log(this.query);
      this.$emit("termChange", this.query);
    },
  },
};
</script>

<style scoped>
input {
  width: 75%;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.125);
}

button {
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.125);
}

div {
  text-align: center;
  margin: 20px;
}

svg {
  width: 20px;
  height: 21px;
}
</style>
