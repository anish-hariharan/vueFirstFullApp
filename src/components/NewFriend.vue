/* eslint-disable */
<template>
  <!-- eslint-disable-next-line vue/max-attributes-per-line -->
  <form action="" @submit.prevent="save">
    <div>
      <label for="">Name</label>
      <input type="text" v-model="enteredName" />
    </div>
    <div>
      <label for="">Phone</label>
      <input type="tel" v-model="enteredPhone" />
    </div>
    <div>
      <label for="">Email</label>
      <input type="email" v-model="enteredMail" />
    </div>
    <div>
      <button>Add Contact</button>
    </div>
  </form>
</template>

<script>

export default {
  emits: ["add-contact"],
  data() {
    return {
      enteredName: "",
      enteredPhone: "",
      enteredMail: "",
    };
  },
  methods: {
    save() {
      this.$emit(
        "add-contact",
        this.enteredName,
        this.enteredPhone,
        this.enteredMail
      );
    },
  },
};
</script>
