<template>
    <div class='signIn' ref="signIn">
        <img class="logo" src="./logo.1.png" />
        <div class="content">
            <div>
                <p>用户名</p>
                <div class="telDiv">
                    <input class="tel" type="text" v-model='tel' placeholder="请输入手机号">
                </div>
            </div>
            <div>
                <p>密码</p>
                <div class="telDiv">
                    <input class="tel" type="password" v-model="password" placeholder="请输入密码">
                </div>
            </div>
        </div>
        <div class="login" @click="login">
            登录
        </div>
        <div class="login" style="margin-left: 150px" @click="register">
            注册
        </div>
    </div>
</template>

<script>
// import $store from '../../store/index'
import {customers} from "@/sqlMap.js";
export default {
  data() {
    return {
      tel: "",
      password: "",
      message: "",
      show: true,
      count: "",
      timer: null,
      TIME_COUNT: "60",
      canClick: true
    };
  },

  methods: {
    register() {
      this.$router.push({ name: "register" });
    },
    login() {
    
        var sql=  customers.login.replace('?',this.tel).replace('?',this.password)
        this.$hp.post("action", {sql:sql}).then(res => {
            if (res.data.length == 0) {
              this.$message({
                showClose: true,
                message: "账号密码错误",
                type: "error"
              });
            } else {
              localStorage.setItem("userInfo",JSON.stringify(res.data[0]) );
              setTimeout(() => {
                window.location.href = "/";
              }, 1000);
            }
          });
      
    }
  }
};
</script>
<style lang='less' scoped>
.signIn {
  // background: rgb(247,247,247);
  height: 100%;
}
.logo {
  width: 100%;
}
.content {
  padding-left: 8%;
  padding-right: 8%;
}

p {
  font-size: 16px;
  color: #131313;
  margin-bottom: 28px;
  margin-top: 40px;
  padding: 0 1%;
}

.telDiv {
  width: 98%;
  padding: 0 1%;
  border-bottom: #dddddd 1px solid;
}

.tel {
  padding-bottom: 10px;
  color: rbga(102, 102, 102, 0.7);
  font-size: 15px;
  width: 100%;
  background: none;
  border: 0px;
}

.left {
  float: left;
}

.login {
  margin-top: 135px;
  /*margin-left: auto;*/
  /*margin-right: auto;*/
  left: 30%;
  right: 50%;
  transform: translate(-50%, -50%);
  position: absolute;
  width: 30%;
  height: 35px;
  background: #ff9e10;
  color: #ffffff;
  font-size: 16px;
  border-radius: 20px;
  text-align: center;
  line-height: 35px;
}
</style>