<template>
   <router-link :to="artistLink">
     <span class="col-lg-1">
        <img class="thumb-image" :src=user.images[0].url alt="">
      </span>
      <h5 class="col-lg-11">
        {{user.name}}
      </h5>
   </router-link>
</template>

<script>
export default {
  name: 'UserItem',
  components: { },
  data() {
    return {
 
    }
  },
  props: {
    user:{ type: Object, required: true}
  },
  computed: {
    artistLink(){
      return `/artist/${this.user.id}`
    }
  },

}
</script>

<style scoped>
  span{display: inline-block;float:left;}
  h5{padding-left: 15px;}
</style>