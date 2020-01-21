<template>
  <div class="mod-albums">
    <div class="hd log url">
      <h2>新歌速递</h2>
      <router-link :to="{ name:'MoreList',params:{ musictype:type, title:title} }" tag="div">更多</router-link>
    </div>
    <div class="container">
      <div class="gallery">
        <div class="scroller">
          <router-link tag="div" :to="{ name:'MusicPlay', params:{songid:item.song_id}}" class="card url" v-for="(item,index) in NewsMusic" :key="index">
            <div class="album">
              <img :src="item.pic_big" :alt="item.title" />
              <div class="name">{{ item.title }}</div>
              <div class="author">{{ item.artist_name }}</div>
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
      NewsMusic: []
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
      default: "1"
    }
  },
  mounted() {
    //  var url = this.HOST + '/v1/restserver/ting?method=baidu.ting.search.catalogSug&query=你'
    var url = "/v1/restserver/ting";
    this.$axios
      .get(url, {
        params: {
          method: "baidu.ting.billboard.billList",
          type: 1,
          size: 3,
          offset: 0
        }
      })
      .then(res => {
        this.NewsMusic = res.data.song_list;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style scoped>
.mod-albums {
  background: #fff;
  padding: 10px 17px;
  margin-top: 10px;
}
.mod-albums .hd {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.hd h2 {
  font-size: 20px;
}
.hd div {
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
.mod-albums .gallery .card .author {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  color: #999;
  font-size: 12px;
  line-height: 12px;
}
</style>