<template>
  <div class="cartcontrol">
    <transition name="slide-fade">
      <div class="cart-decrease" v-show="food.count > 0"
           @click="decreaseCart($event)">
        <span class="inner icon-remove_circle_outline"></span>
      </div>
    </transition>
    <div class="cart-count" v-show="food.count > 0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click="addCart($event)"></div>
  </div>
</template>

<script>
  export default {
    props: {
      food: {
        type: Object
      }
    },
    created() {

    },
    methods: {
      addCart(event) {
        if(!event._constructed) {
          return;
        }

        if(!this.food.count) {
          this.$set(this.food, 'count', 1);
        }else {
          this.food.count++;
        }
      },
      decreaseCart(event) {
        if(!event._constructed) {
          return;
        }

        if(this.food.count > 0) {
          this.food.count--;
        }
      }
    }

  }
</script>

<style lang="stylus">
  .cartcontrol
    font-size: 0
    .cart-decrease
      display: inline-block
      padding: 6px
      transition: all .7s ease-in
      &.slide-fade-enter-active
        transition: all .4s ease
      &.slide-fade-leave-active
        transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0)
      &.slide-fade-enter, &.slide-fade-leave-to
        transform: translate3D(24px, 0, 0)
        opacity: 0
      .inner
        display: inline-block
        line-height: 24px
        font-size: 24px
        color: rgb(0, 160, 220)
    .cart-count
      display: inline-block
      vertical-align: top
      width: 12px
      padding-top: 6px
      line-height: 24px
      text-align: center
      font-size: 10px
      color: rgb(147, 153, 159)
    .cart-add
      display: inline-block
      padding: 6px
      line-height: 24px
      font-size: 24px
      color: rgb(0, 160, 220)

</style>
