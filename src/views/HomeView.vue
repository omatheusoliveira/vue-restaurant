<template>
  <div class="home">
    <CategoryMenu />
    <ItemsList />
    <PaymentCart />
  </div>
</template>

<script>
// @ is an alias to /src
import CategoryMenu from "@/components/CategoryMenu.vue";
import ItemsList from "@/components/ItemsList.vue";
import PaymentCart from "@/components/PaymentCart.vue";

export default {
  name: "HomeView",
  components: {
    CategoryMenu,
    ItemsList,
    PaymentCart,
  },
};
</script>

<style scoped lang="less">
.home {
  display: flex;

  @media @tablets{
    flex-direction: column;
  }
}
</style>
