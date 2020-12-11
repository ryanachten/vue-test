<template>
  <li>
    <h2>{{ name }} {{ isFavourite ? '(Favourite)' : '' }}</h2>
    <button @click="togglefavourite">Toggle favourite</button>
    <button @click="toggleDetails">Show details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone: </strong> {{ phone }}</li>
      <li><strong>Email: </strong> {{ email }}</li>
    </ul>
  </li>
</template>

<script lang="ts">
export default {
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
    isFavourite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emits: {
    'toggle-favourite': (id: string) => id,
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    togglefavourite() {
      this.$emit('toggle-favourite', this.id);
    },
  },
};
</script>

<style>
</style>
