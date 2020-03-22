<template>
  <div class="storegrid">
    <transition-group name="items" tag="section" class="content">
      <div v-for="item in filteredprice" :key="item.id" class="item">
        <div class="img-contain">
            <img :src="`/products/${item.img}`" />
        </div>
        <h3>{{ item.name }}</h3>
        <h4 class="price">{{ item.price | dollar }}</h4>
          <p class="quantity">
            <button class="update-num" @click="quantity > 0 ? quantity-- : quantity = 0">-</button>
            <input type="number" v-model="quantity" />
            <button class="update-num" @click="quantity++">+</button>
          </p>
        <p>
          <button class="button purchase" @click="cartAdd">Add to Cart</button>
        </p>
      </div>
    </transition-group>
    <aside>
      <h3>Thanks for choosing us!</h3>
      <p>Blurp about Pilcrow and Interval</p>
    </aside>
  </div>
</template>

<script>
import StarRating from "vue-star-rating/src/star-rating.vue";
import { mapState } from "vuex";

export default {
  props: {
    data: {
      required: true
    }
  },
  data() {
    return {
      min: 0,
      max: 200,
      pricerange: 200,
      id: this.$route.params.id,
      quantity: 1,
      tempcart: [] // this object should be the same as the json store object, with an additional param, quantity
    };
  },
  computed: {
    filteredprice() {
      return this.data.filter(el => el.price < this.pricerange);
    }
  },
  components: {
    StarRating
  },
    methods: {
    cartAdd() {
      let item = this.product;
      item.quantity = this.quantity;
      this.tempcart.push(item);
      this.$store.commit("addToCart", {...item});
    }
  }
};
</script>

<style lang="scss" scoped>
.content {
  height: 100%;
  width: 100%;
}

.img-contain {
  max-height: 200px;
  max-width: 200px;
  display: flex;
  align-content: center;
  align-items: center;
  img {
    width: 100%;
  }
}

.quantity {
  display: flex;
}

.item {
  max-height: 500px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 20px 0;
}

aside {
  height: 100%;
  width: 100%;
}

.max {
  display: inline-block;
  float: right;
}

.update-num {
  background: black;
  border-color: black;
  color: white;
  font-size: 20px;
  width: 45px;
}

</style>