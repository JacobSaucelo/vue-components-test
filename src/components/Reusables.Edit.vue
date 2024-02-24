<template>
  <div>
    <h2>Edit Item</h2>
    <input v-model="editedItem" type="text" />
    <button @click="save">Save</button>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      editedItem: this.item,
    };
  },
  methods: {
    save() {
      this.$emit("save", this.editedItem);
    },
  },
};
</script>
