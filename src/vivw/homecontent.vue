<template>
  <div class="content_wrapper">
      <div class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide" v-for="item,index in childMsg.slider">
              <a :href='item.linkUrl' >
                <img :src='item.picUrl'/>
              </a>
            </div>
        </div>
        <!-- 如果需要分页器 -->
        <div class="swiper-pagination"></div>
      </div>
      <div class="mod_twocol_list">
        <h2 class="list_title">电台</h2>
        <ul class="list_container">
          <li class="js_play_radio" v-for='item,index in childMsg.radioList'>
            <a href="javascript:;" class="list_main">
              <div class="list_media">
                  <img class="list_pic" :src="item.picUrl" alt="">
                  <span class="icon icon_play"></span>
              </div>
              <div class="list_info">
                  <h3 class="list_tit tit_two_row">{{item.Ftitle}}</h3>
              </div>
            </a>
          </li>
        </ul>
      </div>
      <div class="mod_twocol_list">
        <h2 class="list_title">热门歌单</h2>
        <ul class="list_container">
          <li v-for='item,index in childMsg.songList'>
              <a href="javascript:;" class="list_main">
                <div class="list_media">
                  <img :src="item.picUrl">
                  <span class="listen_count"><i class="icon icon_listen"></i>{{tools.pasNum(item.accessnum)}}</span>
                  <span class="icon icon_play js_play_songlist" data-id="2646688496"></span>
                </div>
                <div class="list_info">
                    <h3 class="list_tit">{{item.songListDesc}}</h3>
                    <p class="list_text">{{item.songListAuthor}}</p>
                </div>
              </a>
          </li>
        </ul>
      </div>
    </div>
</template>

<script>
export default {
  name: 'homecontent',
  props: ['childMsg'],
  watch: {
    childMsg(){
      this.$nextTick(() => {
         var mySwiper = new Swiper('.swiper-container', {
           direction: 'horizontal',
           loop: true,
           pagination: '.swiper-pagination',
           effect : 'coverflow',
           autoplay : 3000,
           paginationClickable :true,
         })
       })
    }
  },
  mounted(){

  },
  data () {
    return {

    }
  }
}
</script>
<style>
  #app .swiper-pagination-bullet-active{
    background:rgba(255,255,255,.8);
  }
</style>