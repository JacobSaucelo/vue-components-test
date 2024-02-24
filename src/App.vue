<template>
  <div id="app">
    <h2>List of Items</h2>
    <ListComponent
      :items="items"
      @edit="editItem"
      @delete="deleteItem"
    ></ListComponent>
    <EditItemComponent
      v-if="selectedItem"
      :item="selectedItem"
      @save="saveItem"
    ></EditItemComponent>
    <AddItemComponent @add="addItemToList"></AddItemComponent>
  </div>
</template>

<script>
import ListComponent from "./components/Reusables.Lists.vue";
import AddItemComponent from "./components/Reusables.Add.vue";
import EditItemComponent from "./components/Reusables.Edit.vue";

export default {
  components: {
    ListComponent,
    AddItemComponent,
    EditItemComponent,
  },
  data() {
    return {
      items: ["Item 1", "Item 2", "Item 3"],
      selectedItem: null,
    };
  },
  methods: {
    editItem(item) {
      this.selectedItem = item;
    },
    saveItem(updatedItem) {
      const index = this.items.indexOf(this.selectedItem);
      if (index !== -1) {
        this.items.splice(index, 1, updatedItem);
        this.selectedItem = null;
      }
    },
    addItemToList(item) {
      this.items.push(item);
    },
    deleteItem(index) {
      this.items.splice(index, 1);
    },
  },
};
</script>
