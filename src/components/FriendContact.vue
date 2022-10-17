<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="favoriteToggle">Toggle Favorite</button>
    <button @click="toggleButton">
      {{ listIsVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="listIsVisible">
      <li><strong>Phone:</strong>{{ phone }}</li>
      <li><strong>Email:</strong> {{ email }}</li>
    </ul>
    <button @click="$emit('delete', id)">Delete</button>
  </li>
</template>
<script>
export default {
  // props: ["id", name", "phone", "email","isFavorite"],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phone: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      // default: "0",
      // validator(value) {
      //   return value === "1" || value === "0";
      // },
    },
  },
  emits: ["toggle-favorite"],
  // emits: {
  //   "toggle-favorite": function(id){}
  // },
  data() {
    return {
      listIsVisible: false,
      // friendIsFavorite: this.isFavorite,
    };
  },
  methods: {
    toggleButton() {
      this.listIsVisible = !this.listIsVisible;
    },
    favoriteToggle() {
      this.$emit("toggle-favorite", this.id);
      // this.friendIsFavorite = !this.friendIsFavorite;
    },
  },
};
</script>
<style scoped></style>
