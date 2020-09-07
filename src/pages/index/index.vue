<template>
  <view class="index">
    <text>{{ msg }}</text>
    <button @tap="onTapOpenid">获取openid</button>
  </view>
</template>

<script>
import { ref } from 'vue'
import './index.less'

export default {
  setup () {
    const msg = ref('Hello world')

    const onTapOpenid = () => {
      wx.cloud.callFunction({
      name: 'login',
      data: {},
      success: res => {
        console.log('[云函数] [login] user openid: ', res.result.openid)
      },
      fail: err => {
        console.error('[云函数] [login] 调用失败', err)
      }
    })
    }

    return {
      msg,
      onTapOpenid,
    }
  }
}
</script>
