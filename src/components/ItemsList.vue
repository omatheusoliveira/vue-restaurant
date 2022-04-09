<template>
  <div class="items-list">
    <ItemBurguer v-for="item in itemsList" :key="item.id" :item="item" />
  </div>
</template>

<script>
import axios from "axios";
import ItemBurguer from "./Item";
export default {
  name: "ItemsList",
  components: {
    ItemBurguer,
  },
  data() {
    return {
      itemsList: [],
    };
  },
  created() {
    axios.get("http://localhost:3000/burguers").then((response) => {
      this.itemsList = response.data;
    });
  },
};
</script>

<style lang="less" scoped>
.items-list {
  margin: 50px;
  display: flex;

  @media @tablets {
    flex-wrap: wrap;
    margin: 20px;
  }

}
</style>
