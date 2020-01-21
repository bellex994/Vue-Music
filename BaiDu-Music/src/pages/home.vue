<template>
 <div>
     <TodayRecommend title="今日推荐" type="2" />
     <NewsMusic title="新歌速递" type="1"/>
     <SwiperBanner/>
     <MusicListNav/>
     <keep-alive>
       <router-view></router-view>
     </keep-alive>
     <TodayRecommend title="热门歌单" type="24" />
 </div>
</template>

<script>
import TodayRecommend from '@/components/Today_Recommend'
import NewsMusic from '@/components/News_Music'
import SwiperBanner from '@/components/Swiper_Banner'
import MusicListNav from './musiclist/music_listnav'

 export default {
   data () {
     return {

     }
   },
   components: {
     TodayRecommend,
     NewsMusic,
     SwiperBanner,
     MusicListNav
   }
 }
</script>

<style>
 
</style>
