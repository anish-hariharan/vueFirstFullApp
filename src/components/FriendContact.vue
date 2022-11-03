<template>
  <li>
    <h2>{{ name }} {{ isFavourite ? "★" : " " }}</h2>
    <button @click="$emit('toggle-favourite', id)">
      {{ !isFavourite ? "Add" : "Remove" }} Favourite
    </button>
    <button @click="$emit('visible', id)">{{ !isVisible ? "Show" : "Hide" }} details</button>
    <ul v-if="isVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>
          {{ emailA }}
        </strong>
      </li>
    </ul>
    <button @click="$emit('delete', id)" >Delete</button>
  </li>
</template>

<script>
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
    phoneNumber: {
      type: String,
      required: true,
    },
    emailA: {
      type: String,
      required: true,
    },
    isFavourite: {
      type: Boolean,
      required: false,
      default: false,
    },
    isVisible: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emits: ["toggle-favourite", "delete"],
};
</script>
