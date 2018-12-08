<template>
    <div class='cartcontrol'>
        <transition name="move">
            <div class='cart-decrease' v-show='food.count>0' @click.stop="decreaseCart($event)">
                <span class='inner icon-remove_circle_outline'></span>
            </div>
        </transition>
        <div class='cart-count' v-show='food.count>0'>{{food.count}}</div>
        <div class='cart-add icon-add_circle' @click.stop="addCart($event)"></div>
    </div>
</template>
<script type="text/javascript">
    import Vue from "vue"
    export default{
        name:'control',
        data(){
            return{

            }
        },
        methods:{
            decreaseCart(e){
                if(!e._constructed){
                    return
                }
                if(this.food.count){
                    this.food.count --
                }
            },
            addCart(e){
                if(!e._constructed){
                    return
                }
                if(!this.food.count){
                    Vue.set(this.food,"count",1)
                }else{
                    this.food.count ++
                }
                
            }
        },
        props:{
            food:{
                type:Object
            }
        },
        
    }
</script>
<style lang="stylus" rel="stylesheet/stylus">
    .cartcontrol
      font-size:0
      .cart-decrease     
        display:inline-block
        padding:6px
        opacity: 1
        transform: translate3d(0, 0, 0)
        .inner
          display:inline-block
          font-size:24px
          line-height:24px
          color:rgb(0,160,220)
          transition: all 0.4s linear
          transform: rotate(0)
        &.move-enter-active, &.move-leave-active
          transition: all 0.4s linear
        &.move-enter, &.move-leave-active
          opacity: 0
          transform: translate3d(24px, 0, 0)
          .inner
            transform: rotate(180deg)
      .cart-count
        display:inline-block
        font-size:10px
        width:12px
        padding-top:6px
        line-height:24px
        text-align:center
        color:rgb(147,153,159)
        vertical-align:top
      .cart-add
        display:inline-block
        padding:6px
        font-size:24px
        line-height:24px
        color:rgb(0,160,220)
        
        
      
        
        
</style>