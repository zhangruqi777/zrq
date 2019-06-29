<template>
    <div>
        <div id="slider" class="mui-slider">
        
				<div id="sliderSegmentedControl" class="mui-scroll-wrapper mui-slider-indicator mui-segmented-control mui-segmented-control-inverted">
					<div class="mui-scroll">
                                <!-- <a :class="['mui-control-item', item.id == 0 ? 'mui-active' : '']" v-for="item in cates" :key="item.id" @tap="getPhotoListByCateId(item.id)">
                            {{ item.title }}
                          </a> -->
		                <a class="mui-control-item mui-active" href="#item1mobile" data-wid="tab-top-subpage-1.html">
							推荐
						</a>
						<a class="mui-control-item" href="#item2mobile" data-wid="tab-top-subpage-2.html">
							热点
						</a>
						<a class="mui-control-item" href="#item3mobile" data-wid="tab-top-subpage-3.html">
							北京
						</a>
						<a class="mui-control-item" href="#item4mobile" data-wid="tab-top-subpage-4.html">
							社会
						</a>
						<a class="mui-control-item" href="#item5mobile" data-wid="tab-top-subpage-5.html">
							娱乐
						</a>
						<a class="mui-control-item" href="#item6mobile" data-wid="tab-top-subpage-6.html">
							科技
						</a>
					</div>
				</div>

			</div>


    <!-- 图片列表区域 -->
    <ul class="photo-list">
      <router-link v-for="item in list" :key="item.id" :to="'/home/photoinfo/' + item.id" tag="li">
        <img v-lazy="item.img_url">
        <div class="info">
          <h1 class="info-title">{{ item.title }}</h1>
          <div class="info-body">{{ item.zhaiyao }}</div>
        </div>
      </router-link>
    </ul>

    
    
    
    </div>
</template>

<script>
import mui from '../../lib/mui/js/mui.min.js'


export default {
    data(){
        return {
            cates:[],
            list:[]
        }
    },
    created(){
        this.getAllCategory();
        this.getPhotoListByCateId();
        
    },
    mounted(){
        mui('.mui-scroll-wrapper').scroll({
        deceleration:0.0005
    })

    },
    methods:{
        getAllCategory() {
          // 获取所有的图片分类
          this.$http.get("api/getimgcategory").then(result => {
            if (result.body.status === 0) {
              // 手动拼接出一个最完整的 分类列表
              result.body.message.unshift({ title: "全部", id: 0 });
              this.cates = result.body.message;
            }
          });
        },
        getPhotoListByCateId(cateId) {
      // 根据 分类Id，获取图片列表
            this.$http.get("api/getimages/" + cateId).then(result => {
                if (result.body.status === 0) {
                    this.list = result.body.message;
                }
            });
        }    

    },
}
</script>

<style lang="scss" scoped>
*{
    touch-action:pan-y;
}

.photo-list {
  list-style: none;
  margin: 0;
  padding: 10px;
  padding-bottom: 0;
  li {
    background-color: #ccc;
    text-align: center;
    margin-bottom: 10px;
    box-shadow: 0 0 9px #999;
    position: relative;
    img {
      width: 100%;
      vertical-align: middle;
    }
    img[lazy="loading"] {
      width: 40px;
      height: 300px;
      margin: auto;
    }

    .info {
      color: white;
      text-align: left;
      position: absolute;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.4);
      max-height: 84px;
      .info-title {
        font-size: 14px;
      }
      .info-body {
        font-size: 13px;
      }
    }
  }
}
</style>
