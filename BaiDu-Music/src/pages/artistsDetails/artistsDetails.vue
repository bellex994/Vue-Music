<template lang="html">
  <div class="">
    <Title :avatar="this.$route.params.avatar" :name="this.$route.params.name" />
    <List :ting_uid="this.$route.params.ting_uid"/>
  </div>
</template>

<script>
import Title from '@/components/details/title'
import List from '@/components/details/list'

export default {
  data(){
    return{
      avatar: '',
      name: ''
    }
  },
  components:{
    Title,
    List
  }
}
</script>

<style>
</style>
