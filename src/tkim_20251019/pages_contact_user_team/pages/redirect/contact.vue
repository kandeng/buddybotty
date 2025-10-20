<template>
  <view></view>
</template>

<script>
export default {
  onLoad() {
    // 重定向到分包中的实际页面
    uni.redirectTo({
      url: '/pages_contact_user_team/NEUIKit/pages/Contact/index'
    })
  }
}
</script>