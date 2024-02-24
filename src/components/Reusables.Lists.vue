<template>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ item }}
        <button @click="editItem(item)">Edit</button>
        <button @click="deleteItem(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    editItem(item) {
      this.$emit("edit", item);
    },
    deleteItem(index) {
      this.$emit("delete", index);
    },
  },
};
</script>
