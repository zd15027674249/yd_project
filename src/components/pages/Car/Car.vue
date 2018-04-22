<template>
  <div class="not-found page">
      <div class="nav">
        <div class="back">
          <i class="fa fa-chevron-left" aria-hidden="true"></i>
        </div>
        <div class="text">购物车</div>
        <div class="bj" href="">
          <span>编辑</span>
        </div>
      </div>
      <cell 
			v-for = "friut in cars"
			:key = "friut.id"
			:title = "friut.product_name"
			:label = "friut.price +'/'+ friut.volume+' * '+friut.num"
			:src = "friut.bphoto"
		>
			<mz-button @click ="reduceGoodInCar(friut)" type="danger" size = "small">-</mz-button>
			<mz-button @click="addGoodInCar(friut)" type="danger" size = "small">+</mz-button>
		</cell>
		<total></total>
  </div>
</template>

<script>
import Cell from "../../../mz-ui/Cell/Cell"
import Total from "./Total";
import { mapState, mapActions } from 'vuex'
export default {
  name: 'Car',
  components: {Total,Cell},
		computed:{
			...mapState({
				cars: state => state.buycar.cars
			})
		},
		methods: {
			...mapActions(['addGoodInCar', 'reduceGoodInCar'])
		},
		mounted () {
			console.log(this)
		}
}
</script>

<style lang="scss" scoped>
  .nav{
    background-color: #fff;
    color:#75a739;
    height: .45rem;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    .back{
      display: inline-block;
      i{
        width: .4rem;
        color: #75a739;
        display: inline-block;
        font-size: .22rem;
        text-align: center;
        padding-left: 0.07rem;
      }
    }
    .text{
        display: inline-block;
        text-align: center;
        font-size: .17rem;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        width: 2.4rem;
        margin-top: 0.1rem;
        font-weight: normal;
    }
    .bj{
        height: 0.43rem;
        text-align:right;
        font-size: 0.14rem;
        display: inline-block;
        float: right;
        line-height: 0.43rem;
        margin-right: 0.2rem;
    }
  }
</style>



