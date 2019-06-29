<template>
    <div>
        <ul class="mui-table-view">
            <!-- <li class="mui-table-view-cell mui-media" v-for="item in newslist" :key="item.id">
				<a href="javascript:;">
					上面改成<router-link :to="'/home/nesinfo'+item.i"></router-link>
					<img class="mui-media-object mui-pull-left" :src="item.ing.url">
					<div class="mui-media-body">
						<h4>{{item.title}}</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：{{item.add_time | dateFormat}}</span>
                            <span>点击：{{item.click}}</span>
                        </p>
					</div>
				</a>
			</li> -->
			<li class="mui-table-view-cell mui-media">
				<a href="#">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
			<li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
            <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
            <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
            <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
                        <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
                        <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
                        <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
                        <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
                        <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
                        <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
                        <li class="mui-table-view-cell mui-media">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" src="../../images/lufei.jpg">
					<div class="mui-media-body">
						<h4>幸福</h4>
						<p class='mui-ellipsis'>
                            <span>发表时间：201</span>
                            <span>点击：0次</span>
                        </p>
					</div>
				</a>
			</li>
		</ul>
    </div>
</template>

<script>

import {Toast} from 'mint-ui'
export default {
    data(){
        return {
            newslist:[]
        }
    },
    created(){
        this.getNewsList()
    },
    methods:{
        getNewsList(){
            this.$http.get('api/getnewslist').then(result=>{
                if(result.body.status===0){
                    this.newslist=result.body.message;
                }else{
                    Toast('获取新闻列表失败');
                }
            })
        }
    }
}
</script>

<style lang="scss" scoped>
  .mui-table-view {
      h3 {
          font-size: 14px
      }
      .mui-ellipsis {
          font-size: 12px;
        //   color: #226aff;
          display: flex;
          justify-content: space-between;
      }
  }
</style>

