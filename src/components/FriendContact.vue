<template>
  <li>
    <h2>{{ name }}{{ friendIsFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ buttonVisible ? "Hide" : "Show" }}
      Details
    </button>
    <button @click="toggleFavorite">
      Toggle Favorite
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone: </strong>{{ phoneNumber }}</li>
      <li><strong>Email: </strong>{{ emailAddress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      // validator: function(value) {
      //   return value === true || value === false
      // },
    },
  },
  data() {
    return {
      detailsAreVisible: false,
      buttonVisible: false,
      friendIsFavorite: this.isFavorite,
    }
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
      this.buttonVisible = !this.buttonVisible
    },
    toggleFavorite() {
      this.friendIsFavorite = !this.friendIsFavorite
    },
  },
}
</script>
