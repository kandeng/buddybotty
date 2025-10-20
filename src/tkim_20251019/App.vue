<script lang="ts">
// Lazy load both RootStore and NIM SDK
export default {
  onLaunch() {
    const imOptions = {
      appkey: '8c99fe4133bf68eeb92b17246ab6d206', // 请填写您的 appkey
      account: 'tungkong_20251017', // 请填写您的 account
      token: '1234567890', // 请填写您的 token
    }
    if (imOptions) {
      this.initNim(imOptions)
    } else {
      // 需要登录, 跳转登录页
    }
  },
  methods: {
    async initNim(opts) {
      // Lazy load NIM SDK and RootStore only when needed
      const [{ NIM, V2NIMConst }, { setAdapters, uniAppAdapters }, RootStore] = await Promise.all([
        import('./nim.js'),
        import('nim-web-sdk-ng/dist/esm/nim.js'),
        import('@xkit-yx/im-store-v2')
      ])
      
      // 设置 uniapp 环境
      setAdapters(uniAppAdapters)
      
      const isWxApp = uni.getSystemInfoSync().uniPlatform == 'mp-weixin'
      // 初始化 nim sdk
      const nim = (uni.$UIKitNIM = NIM.getInstance(
        {
          appkey: opts.appkey,
          needReconnect: true,
          debugLevel: 'debug',
          apiVersion: 'v2',
        },
        {
          V2NIMLoginServiceConfig: {
            lbsUrls: isWxApp
              ? ['https://lbs.netease.im/lbs/wxwebconf.jsp']
              : ['https://lbs.netease.im/lbs/webconf.jsp'],
            linkUrl: isWxApp ? 'wlnimsc0.netease.im' : 'weblink.netease.im',
            /**
             * 使用固定设备 ID，
             */
            isFixedDeviceId: true,
          },
        }
      ))
      // 初始化 store
      const store = (uni.$UIKitStore = new RootStore.default(
        nim,
        {
          addFriendNeedVerify: false,
          // 是否需要显示 p2p 消息、p2p 会话列表消息已读未读，默认 false
          p2pMsgReceiptVisible: true,
          // 是否需要显示群组消息已读未读，默认 false
          teamMsgReceiptVisible: true,
          teamAgreeMode:
            V2NIMConst && V2NIMConst.V2NIMTeamAgreeMode ? 
            V2NIMConst.V2NIMTeamAgreeMode.V2NIM_TEAM_AGREE_MODE_NO_AUTH : 0,
          /**
             发送消息前的钩子函数，异步函数,可配置推送参数、拦截消息发送等，返回 false 则不发送消息
          */
          sendMsgBefore: async (options) => {
            const pushConfig = {}
            return { ...options, pushConfig }
          },
        },
        'UniApp'
      ))

      nim.login(opts.account, opts.token).then(() => {
        // 跳转至您需要展示的页面
      })
    },
    logout() {},
  },
}
</script>
<style>
uni-page-body {
  height: 100%;
}
uni-page-body > uni-view {
  height: 100%;
}
</style>
