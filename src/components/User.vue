<template>
  <Layout :has_share="false" title="我的">
    <div class="wrap">
        <mu-list>
          <mu-list-item title="观看历史" to="user/history">
            <mu-icon slot="left" value="history"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
          <mu-list-item title="我的收藏" to="user/favorite">
            <mu-icon slot="left" value="favorite"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
          <mu-list-item title="我的订单" to="user/order">
            <mu-icon slot="left" value="favorite"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
          <mu-list-item title="设置" to="user/settings">
            <mu-icon slot="left" value="settings"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
          <mu-list-item title="关于" to="user/about">
            <mu-icon slot="left" value="timeline"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
          <mu-list-item v-if="user==null" title="登录" to="user/to_login" >
            <mu-icon slot="left" value="timeline"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
           <mu-list-item v-else title="退出" @click="quit">
            <mu-icon slot="left" value="timeline"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
        </mu-list>
          <mu-list-item title="测试" to="user/test">
            <mu-icon slot="left" value="timeline"/>
            <mu-icon slot="right" value="keyboard_arrow_right"/>
          </mu-list-item>
        </mu-list>
    </div>
  </Layout>
</template>

<script>
let _self;
import Layout from '@/components/Layout';

export default {
     data() {
        return {
            user:null
        };
    },
    created() {
        _self = this;
       this.user=JSON.parse(localStorage.getItem('userInfo')) 
    },
    mounted() {
        
    },
    methods: {
        quit(){
            localStorage.removeItem('userInfo')
            this.$router.push({ name: "to_login" });
        }
    },
    computed: {
        
    },
    components: {
        Layout,
    }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">

</style>
