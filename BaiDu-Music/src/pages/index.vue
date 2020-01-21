<template>
 <div class="index">
     <ul>
       <router-link to="/home" tag="li">
         <img src="../assets/logo-ea5.png" alt="">
       </router-link>
       <router-link to="/artists" tag="li">歌手</router-link>
       <router-link to="/listcate" tag="li">榜单</router-link>
       <router-link to="/ucenter" tag="li">我的</router-link>
       <router-link to="/search" tag="li">搜索</router-link>
     </ul>
     <router-view></router-view>
 </div>
</template>

<script>

 export default {
   data () {
     return {

     }
   },
   components: {
    
   }
 }
</script>

<style scoped>
.index ul{
  display: flex;
  height: 50px;
  line-height: 50px;
  background: #f9f9f9;
}
.index ul li{
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}
.index ul li img{
  width: 26px;
  height: 26px;
} 
.index ul li a{
  font-size: 16px;
  color: #999;
}
</style>
