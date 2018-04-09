<template>
  <div class="menu-wrap">
    <div class="top-bar" @click="showMenu">click Me</div>
    <div class="bot-content" v-if="isShowMenu">
      <div class="main-view-item itemI">我</div>
      <div class="main-view-item itemII">没</div>
      <div class="main-view-item itemIII">屙</div>
      <div class="main-view-item itemIV">在</div>
      <div class="main-view-item itemV">屎</div>
      <div class="main-view-item itemVI">啊</div>
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
      isShowMenu: false
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
.top-bar {
  background: #36303f;
  height: 50px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}
.bot-content {
  width: 100%;  
  flex: auto;
  display: flex;
  flex-wrap: wrap;
}
.main-view-item {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50%;
  flex: auto;
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
