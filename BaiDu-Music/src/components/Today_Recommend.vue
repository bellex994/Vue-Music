<template>
  <div class="mod-albums">
    <div class="hd log url">
      <h2>{{ title }}</h2>
      <router-link tag="div" :to="{ name:'MoreList',params:{ musictype:type, title:title} }">更多</router-link>
    </div>
    <div class="container">
      <div class="gallery">
        <div class="scroller">
          <router-link tag="div" :to="{ name:'MusicPlay', params:{songid:item.song_id}}" class="card url" v-for="(item,index) in todayRecommend" :key="index">
            <div class="album">
              <img :src="item.pic_big" :alt="item.title" />
              <div class="name">{{ item.title }}</div>
            </div>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todayRecommend: []
    };
  },
  components: {},
  props: {
    title: {
      type: String,
      default: ""
    },
    type: {
      type: String,
      default: '1'
    }
  },
  mounted() {
    //  var url = this.HOST + '/v1/restserver/ting?method=baidu.ting.search.catalogSug&query=你'
    this.init()
  },
  methods: {
    init() {
      this.getTodayRecommend()
    },
    getTodayRecommend() {
      var url = "/v1/restserver/ting?method='baidu.ting.billboard.billList'&size=6&type=" + this.type + "&offset=0"
      this.$axios.get(url)
        .then(res => {
          this.todayRecommend = res.data.song_list;
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<style scoped>
.mod-albums {
  background: #fff;
  padding: 10px 17px;
}
.mod-albums .hd {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.hd h2 {
  font-size: 20px;
}
.hd > div {
  font-size: 14px;
}
.mod-albums .gallery {
  overflow: hidden;
  margin: 0 -5px;
}

.mod-albums .gallery .card {
  width: 33.3%;
  float: left;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  padding: 0 5px 10px;
}

.mod-albums .gallery .card .album {
  position: relative;
}

.mod-albums .gallery .card img {
  width: 100%;
  height: auto;
  border: 1px solid #eee;
}

.mod-albums .gallery .card .name {
  font-size: 12px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin-top: 4px;
  line-height: 14px;
  max-height: 28px;
  margin-bottom: 2px;
}
</style>
