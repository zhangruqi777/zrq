<template>
    <div class="goods-list">
        <div class="goods-item">
            <img src="//m.360buyimg.com/mobilecms/jfs/t1/71956/31/1792/226949/5d0216a7E2813adcc/b442caf46e8232a4.jpg!q70.jpg" alt="">
            <h1 class="title">
                小米（Mi）小米note 16G
            </h1>
            <div class="info">
            <p class="price">
                <span class="now">¥999</span>
                <span class="old">¥2399</span>
            </p>
            <p class="sell">
                <span>热卖中</span>
                <span>剩60件</span>
            </p>
            </div>
        </div>

        <div class="goods-item">
            <img src="//m.360buyimg.com/mobilecms/jfs/t1/57826/26/3542/486099/5d143848E4028ab7f/abdced8b869efc2f.png" alt="">
            <h1 class="title">
                小米（Mi）小米note 16G
            </h1>
            <div class="info">
            <p class="price">
                <span class="now">¥999</span>
                <span class="old">¥2399</span>
            </p>
            <p class="sell">
                <span>热卖中</span>
                <span>剩60件</span>
            </p>
            </div>
        </div>

        <div class="goods-item">
            <img src="//m.360buyimg.com/mobilecms/jfs/t1/57826/26/3542/486099/5d143848E4028ab7f/abdced8b869efc2f.png" alt="">
            <h1 class="title">
                小米（Mi）小米note 16G
            </h1>
            <div class="info">
            <p class="price">
                <span class="now">¥999</span>
                <span class="old">¥2399</span>
            </p>
            <p class="sell">
                <span>热卖中</span>
                <span>剩60件</span>
            </p>
            </div>
        </div> 

        <div class="goods-item">
            <img src="//m.360buyimg.com/mobilecms/jfs/t1/71956/31/1792/226949/5d0216a7E2813adcc/b442caf46e8232a4.jpg!q70.jpg" alt="">
            <h1 class="title">
                小米（Mi）小米note 16G尼康小米note 16G尼康小米note 16G尼康小米note 16G尼康
            </h1>
            <div class="info">
            <p class="price">
                <span class="now">¥999</span>
                <span class="old">¥2399</span>
            </p>
            <p class="sell">
                <span>热卖中</span>
                <span>剩60件</span>
            </p>
            </div>
        </div> 

<!-- <router-link class="goods-item" v-for="item in goodslist" :key="item.id" :to="'/home/goodsinfo/' + item.id" tag="div">
      <img :src="item.img_url" alt="">
      <h1 class="title">{{ item.title }}</h1>
      <div class="info">
        <p class="price">
          <span class="now">￥{{ item.sell_price }}</span>
          <span class="old">￥{{ item.market_price }}</span>
        </p>
        <p class="sell">
          <span>热卖中</span>
          <span>剩{{ item.stock_quantity }}件</span>
        </p>
      </div>
    </router-link> -->

        <mt-button type="danger" size="large" @click="getMore">加载更多</mt-button>      

    </div>
</template>

<script>
export default {
    data(){
        return {
            pageindex:1,
            goodslist:[]
        }
    },
    created(){
        this.getGoodsList();
    },
    methods:{
        getGoodsList(){
           this.$http.get('api/getgoods?pageindex='+this.pageindex).then(result=>{
               if (result.body.status === 0){
                //    this.goodslist = result.body.message;
                this.goodslist = this.goodslist.concat(result.body.message);
               }
           }) 
        },
        getMore(){
            this.pageindex++;
            this.getGoodsList();   
        },
        
    }
}
</script>

<style lang="scss" scoped>
.goods-list {
    display: flex;
    flex-wrap: wrap;
    padding: 7px;
    justify-content: space-between
}

.goods-item {
    width: 49%;
    border: 1px solid #ccc;
    box-shadow: 0 0 8px #ccc;
    margin: 3px 0;
    padding: 2px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 293px;

    img {
        width: 100%;
    }
    .title {
       font-size: 14px;
    }
    .info {
        background-color: #eee;
        p {
            margin: 0;
            padding: 5px;
        }
        .price{
            .now{
                color: red;
                font-weight: bold;
                font-size: 16px;

            }
            .old{
              text-decoration: line-through;  
              font-size: 12px;
              margin-left: 10px;
            }
        }
        .sell{
            display: flex;
            justify-content: space-between;
            font-size: 13px;
        }
    }
}
</style>

