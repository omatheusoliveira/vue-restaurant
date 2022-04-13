<template>
  <div class="items-list">
    <LoadingAnimation v-if="isLoading" />
    <ItemMenu v-for="item in itemsList" :key="item.id" :item="item" />
  </div>
</template>

<script>
import axios from "axios";
import ItemMenu from "./Item";
import LoadingAnimation from "./LoadingAnimation";
export default {
  name: "ItemsList",
  components: {
    ItemMenu,
    LoadingAnimation,
  },
  data() {
    return {
      itemsList: [],
      isLoading: false,
    };
  },
  created() {},

  computed: {
    selectedCategory() {
      return this.$store.state.selectedCategory;
    },
  },

  methods: {
    getItemList() {
      this.isLoading = true;
      this.itemsList = [];
      setTimeout(() => {
        axios
          .get(`http://localhost:3000/${this.selectedCategory}`)
          .then((response) => {
            this.itemsList = response.data;
            this.isLoading = false;
          });
      }, 500);
    },
  },

  watch: {
    selectedCategory() {
      this.getItemList();
    },
  },
};
</script>

<style lang="less" scoped>
.items-list {
  margin: 50px;
  display: flex;
  width: 100%;

  @media @tablets {
    flex-wrap: wrap;
    margin: 0;
    padding: 20px;
  }
}
</style>
