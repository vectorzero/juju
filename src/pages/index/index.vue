<template>
  <div class="menu-wrap">
    <div class="top-bar" @click="showMenu">
      <div class="menuitem" :class="isActive?'isActive':''"> 
        <span class="line"></span> 
        <span class="line"></span> 
        <span class="line"></span> 
      </div>
    </div>
    <div class="bot-content" v-if="isShowMenu">
      <div class="main-view-item itemI">盲生</div>
      <div class="main-view-item itemII">你</div>
      <div class="main-view-item itemIII">现</div>
      <div class="main-view-item itemIV">发</div>
      <div class="main-view-item itemV">了</div>
      <div class="main-view-item itemVI">华点</div>
    </div>
    <div class="bot-index" v-else>
      <a class="ani-text" href="/pages/counter/main">JuJu</a>
    </div>
  </div>
    
    <!-- <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div>

    <div class="usermotto">
      <div class="user-motto">
        <card :text="motto"></card>
      </div>
    </div>

    <form class="form-container">
      <input type="text" class="form-control" v-model="motto" placeholder="v-model" />
      <input type="text" class="form-control" v-model.lazy="motto" placeholder="v-model.lazy" />
    </form>
    <a href="/pages/counter/main" class="counter">去往Vuex示例页面</a> -->
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello World',
      userInfo: {},
      isShowMenu: false,
      isActive: false
    }
  },

  components: {
    card
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    showMenu() {
      this.isShowMenu = !this.isShowMenu;
      this.isActive = !this.isActive;
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped>
  .menu-wrap {
    display: flex;
    flex-direction: column;
    padding: 0;
    height: 100vh;
    width: 100%;
  }
  .menuitem.isActive{
    transition: all 0.3s ease-in-out;
    transition-delay: 0.6s;
    transform: rotate(45deg);
  }

  .menuitem.isActive .line:nth-child(2){
    width: 0px;
  }

  .menuitem.isActive .line:nth-child(1),
  .menuitem.isActive .line:nth-child(3){
    transition-delay: 0.3s;
  }

  .menuitem.isActive .line:nth-child(1){
    transform: translateY(13px);
  }

  .menuitem.isActive .line:nth-child(3){
    transform: translateY(-13px) rotate(90deg);
  }
  
  .menuitem .line{
    width: 50px;
    height: 5px;
    background-color: #ecf0f1;
    display: block;
    margin: 8px auto;
    transition: all 0.3s ease-in-out;
  }
  .menuitem:hover{
    cursor: pointer;
  }
  .top-bar {
    background: #36303f;
    height: 50px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }
  .bot-index {
    width: 100%;  
    flex: auto;
    display: flex;
    flex-wrap: wrap;
    background: #36303f;
  }
  @keyframes tipsy {
    from {transform: translateX(-50%) translateY(-50%) rotate(0deg);}
    to {transform: translateX(-50%) translateY(-50%) rotate(360deg);}
  }
  .ani-text {
    color: #fffbf1;
    text-shadow: 0 20px 25px #2e2e31, 0 40px 60px #2e2e31;
    font-size: 80px;
    font-weight: bold;
    text-decoration: none;
    letter-spacing: -3px;
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
  }
  .ani-text:before,
  .ani-text:after {
    content: '';
    padding: .9em .4em;
    position: absolute;
    left: 50%;
    width: 100%;
    top: 50%;
    display: block;
    border: 15px solid red;
    transform: translateX(-50%) translateY(-50%) rotate(0deg);
    animation: tipsy 10s infinite alternate ease-in-out;
  }
  .ani-text:before {
    border-color: #d9524a #d9524a rgba(0, 0, 0, 0) rgba(0, 0, 0, 0);
    z-index: -1;
  }
  .ani-text:after {
    border-color: rgba(0, 0, 0, 0) rgba(0, 0, 0, 0) #d9524a #d9524a;
    box-shadow: 25px 25px 25px rgba(46, 46, 49, .8);
  }
  .bot-content {
    width: 100%;  
    flex: auto;
    display: flex;
    flex-wrap: wrap;
    background: #36303f;
  }
  .main-view-item {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50%;
    flex: auto;
    color: white;
  }
  .itemI {
    transform: rotateX(-90deg);
    animation: Xanimation 0.5s forwards;
    transform-origin: 0 0 0;
    background: #635764;
  }
  .itemII {
    transform: rotateY(-90deg);
    animation: Yanimation 0.5s forwards;
    transform-origin: 0 0 0;
    animation-delay: 0.5s;
    background: #7d637d;
  }
  .itemIII {
    transform: rotateY(-90deg);
    animation: Yanimation 0.5s forwards;
    transform-origin: 100% 100% 0;
    animation-delay: 1.5s;
    background: #a3756c;
  }
  .itemIV {
    transform: rotateX(-90deg);
    animation: Xanimation 0.5s forwards;
    transform-origin: 0 0 0;
    animation-delay: 1s;
    background: #b88680;
  }
  .itemV {
    transform: rotateX(-90deg);
    animation: Xanimation 0.5s forwards;
    transform-origin: 0 0 0;
    animation-delay: 2s;
    background: #eaa68f;
  }
  .itemVI {
    transform: rotateY(-90deg);
    animation: Yanimation 0.5s forwards;
    transform-origin: 0 0 0;
    animation-delay: 2.5s;
    background: #f3bdaa;
  }
  @keyframes Xanimation
  {
    from {transform: rotateX(-90deg);}
    to {transform: rotateX(0deg);}
  }
  @keyframes Yanimation
  {
    from {transform: rotateY(-90deg);}
    to {transform: rotateY(0deg);}
  }

  .userinfo {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .userinfo-avatar {
    width: 128rpx;
    height: 128rpx;
    margin: 20rpx;
    border-radius: 50%;
  }

  .userinfo-nickname {
    color: #aaa;
  }

  .usermotto {
    margin-top: 150px;
  }

  .form-control {
    display: block;
    padding: 0 12px;
    margin-bottom: 5px;
    border: 1px solid #ccc;
  }

  .counter {
    display: inline-block;
    margin: 10px auto;
    padding: 5px 10px;
    color: blue;
    border: 1px solid blue;
  }
</style>
