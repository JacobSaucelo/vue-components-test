<template>
  <div>
    <input v-model="newItem" type="text" />
    <button @click="addItem">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
    };
  },
  methods: {
    addItem() {
      if (this.newItem.trim() !== "") {
        this.$emit("add", this.newItem);
        this.newItem = "";
      }
    },
  },
};
</script>
