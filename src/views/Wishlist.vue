<template>
  <div class="container">
    <div v-if="addToCartSuccess" class="text-center mr-5">
      <div class="alert alert-success alert-dismissible">
        <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
        <strong>Success</strong> {{addToCartSuccess}}
      </div>
    </div>
    <div v-if="addToCartFailed" class="text-center mr-5">
      <div class="alert alert-danger alert-dismissible">
        <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
        <strong>Failed!</strong> {{addToCartFailed}}
      </div>
    </div>
    <div class="row" v-if="!wishlists.length">
      <img src="https://2.bp.blogspot.com/-QfSOClZc8r0/XNr6srFlzjI/AAAAAAAAGlA/lzs505eFFiEdyAytzKkMabdUTihKywcqwCLcBGAs/s1600/EXAM360%2B-%2BNo%2BWishlist.png" width="800">
    </div>
    <div class="row" v-else>
      <WishlistCard
      v-for="(wishlist, i) in wishlists"
      :key="i"
      :wishlist="wishlist"></WishlistCard>
    </div>
  </div>
</template>

<script>
import WishlistCard from '../components/WishlistCard'
export default {
  name: 'Wishlist',
  components: {
    WishlistCard
  },
  computed: {
    wishlists () {
      return this.$store.state.wishlist
    },
    addToCartSuccess () {
      return this.$store.state.addToCartSuccess
    },
    addToCartFailed () {
      return this.$store.state.addToCartFailed
    }
  },
  created () {
    this.$store.dispatch('getWishlist')
  }
}
</script>

<style>

</style>
