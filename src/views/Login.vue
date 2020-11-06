<template>
  <div>
    <div class="head">
      <div class="center">
        <div class="left_logo"></div>
        <div class="right_nav">
          <span>申请使用</span>
          <span>官网</span>
          <span>周边</span>
          <span>公众号</span>
        </div>
      </div>
    </div>
    <div class="body">
      <div class="left_ban">
      </div>
      <div class="login_form">
      <div class="login_method">
        <span class="phone"  @click="switchLogin(1)">手机号码登录</span>
        <span class="phone" style="margin-left:60px" @click="switchLogin(2)">账号登录</span>
        </div>
        <div v-if="!loginWay">
        <div class="line" v-if="!loginWay"></div>
          <div id="errorbox1">
            <input type="text" class="input_text" v-model="phone"
              placeholder="请输入手机号" /><br>
          </div>
          <div class="errorbox">{{error_phone}}</div>
          <div>
            <input type="password" class="input_text" v-model="password"
              placeholder="请输入密码" /><br>
          </div>
          <div class="errorbox">{{error_password}}</div>
          <button class="login_btn" id="login_btn" @click="login_phone()">登录</button>
        </div>
          <div v-if="loginWay">
        <div class="line1" v-if="loginWay" ></div>
          <div id="errorbox1">
            <input type="password" class="input_text"
              placeholder="请输入登录名" v-model="username" /><br>
          </div>
           <div class="errorbox">{{error_username}}</div>
          <div>
            <input type="password" class="input_text"
              placeholder="请输入密码" v-model="password"/><br>
          </div>
          <div  class="errorbox">{{error_password}}</div>
           <button class="login_btn" id="login_btn" @click="login_acc()">登录</button>
        </div>
      </div>
    </div>
    <div class="foot">
      <ul class="product">
        <li style="list-style: none;">
          <div class="img1">
            <div class="font">
              <img src="https://prox.schoolpal.cn/common/images/icon-scp.png" height="40px" width="40px" />
              <ul>
                <li style="list-style: none;" class="font1">校宝收银宝</li>
                <li style="list-style: none;" class="font2">学校收费标准</li>
              </ul>
            </div>
          </div>
        </li>
        <li style="list-style: none;">
          <div class="img2">
            <div class="font">
              <img src="https://prox.schoolpal.cn/common/images/icon-zhaoshengbao.png" height="40px" width="40px" />
              <ul>
                <li class="font1" style="list-style: none;">校宝招生宝</li>
                <li class="font2" style="list-style: none;">一站招生服务</li>
              </ul>
            </div>
          </div>
        </li>
        <li style="list-style: none;">
          <div class="img3">
            <div class="font">
              <img src="https://prox.schoolpal.cn/common/images/icon-anxinbao.png" height="40px" width="40px" />
              <ul>
                <li style="list-style: none;" class="font1">校宝安心宝</li>
                <li style="list-style: none;" class="font2">教育保险精选</li>
              </ul>
            </div>
          </div>
        </li>
      </ul>
      <div class="hot_line">
        <ul>
          <li class="p_li">咨询热线</li>
          <li class="p_li">400-6999-707</li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      loginWay: false,
      phone: '',
      username: '',
      password: '',
      suffix: '',
      error_phone: '',
      error_password: '',
      error_username: ''
    }
  },
  methods: {
    login_acc () {
      if (this.username === '') {
        this.error_username = '用户名不能为空'
        return
      }
      if (this.password === '') {
        this.error_password = '密码不能为空'
        return
      }
      this.error_username = ''
      this.error_password = ''
      alert('登录成功' + ' 用户名:' + this.username + ' 密码: ' + this.password)
    },
    login_phone () {
      if (this.phone === '') {
        this.error_phone = '手机号码不能为空'
        return
      }
      if (this.phone.length < 11) {
        this.error_phone = '手机号码格式不正确'
        return
      }
      if (this.password === '') {
        this.error_phone = ''
        this.error_password = '密码不能为空'
        return
      }
      this.error_phone = ''
      this.error_password = ''
      alert('登录成功' + ' 手机号码:' + this.phone + ' 密码:' + this.password)
    },
    switchLogin (index) {
      if (index === 1) {
        this.error_phone = ''
        this.username = ''
        this.password = ''
        this.error_password = ''
        this.loginWay = false
      }
      if (index === 2) {
        this.error_username = ''
        this.loginWay = true
        this.password = ''
        this.error_password = ''
        this.phone = ''
      }
    }
  }
}
</script>
<style>
.head{
  display:flex;
  font-size: 16px;
}
.center{
  display: flex;
  justify-content : space-between;
  margin: auto;
}
.left_logo{
  width: 400px;
  height: 60px;
  background:url('https://cdn.schoolpal.cn/schoolpal/resource/ci/SchoolPal-NETCore-PC/130/common/images/icon-loginlogo-new.jpg?version=20201022223932') no-repeat;
}
.right_nav{
  width: 600px;
  height: 60px;
  display: flex;
  justify-content : space-between;
}
.body{
  display: flex;
  background-color: #F2F6FC;
  margin: auto;
  width:1000px;
}
.left_ban{
  width: 560px;
  height: 510px;
  background:url('https://schoolpal.oss-cn-hangzhou.aliyuncs.com/erpbanner/erplogin0827.jpg') no-repeat;
  background-size: contain;
  margin: auto;
}
.login_form{
  height: 100%;
  width: 440px;
  margin-top: 30px;
  border-radius: 8px;
  margin-left: 10px;
}
.input_text{
  display: block;
  border: none;
  background: none !important;
  width: 340px;
  height: 24px;
  font-size: 14px;
  outline: none;
  margin-top: 40px;
  padding-bottom: 10px;
  margin-left: 40px;
}
.msg{
  font-size: 12px;
  color: #ff3366;
}
.phone{
    color: #0B1645;
    font-weight: 500;
    font-size: 18px;
    position: relative
}
.line{
  display: block;
  width: 32px;
  height: 5px;
  background: rgba(0,122,255,1);
  border-radius: 4px;
  margin-left: 125px;
  margin-bottom: 40px;
}
.line1{
  display: block;
  width: 32px;
  height: 5px;
  background: rgba(0,122,255,1);
  border-radius: 4px;
  margin-left: 275px;
  margin-bottom: 40px;
}
.login_btn{
  width: 320px;
  height: 54px;
  margin-left: 40px;
  font-size: 16px;
  background-color: #007AFF;
  border-radius: 32px;
  margin-top: 150px;
  margin-bottom: 30px;
}
.login_btn:hover{
  background-color: #0064dc;
}
.foot{
  width: 1000px;
  display: flex;
  margin-top: 10px;
  justify-content: space-between;
  margin:auto;
  background-color: #F2F6FC;
}
.product{
  display: flex;
  padding: 0px;
}
.img1{
  width: 210px;
  height: 60px;
  display: flex;
  background-color:rgba(245,203,207);
  margin-right: 10px;
  border-radius: 8px;
}
.img2{
  width: 210px;
  height: 60px;
  display: flex;
  background-color: rgba(245,203,207);
  margin-right: 10px;
  border-radius: 8px;
}
.img3{
  width: 210px;
  height: 60px;
  display: flex;
  background-color: rgba(245,203,207);
  margin-right: 10px;
  border-radius: 8px;
}
.font{
  display: flex;
  margin: auto;
  align-content: space-between;
}
.font1{
font-size: 14px;
font: bold;
}
.font2{
  font-size: 12px;
}
.hot_line{
  display: flex;
}
.p_li{
  font-size: 28px;
  list-style-type:none;
  font: bold;
  padding-right: 10px;
}
.errorbox {
  display: flex;
  font-size: 12px;
  color: #ff3366;
  margin-left: 300px;
}
.login_method{
    margin: 56px auto 0;
    width: 260px;
    font-size: 18px;
    color: rgba(0,0,0,.45);
    line-height: 25px;
}
</style>
