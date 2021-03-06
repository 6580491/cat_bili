配置相关
配置使用的 json5，兼容 json 且更加灵活，可以支持 注释。
务必使用 https://verytoolz.com/json5-validator.html 校验 json5 格式（校验不通过无法继续使用）。
Gzip 压缩地址（有说明时才用，一般都不需要用）https://www.baidufe.com/fehelper/en-decode/

配置文件路径
满足以下的目录结构的 config.json{5} 都是符合要求的配置文件路径。
你可以不用文件配置，而是使用环境变量 BILITOOLS_CONFIG（同样的配置，但需要 gzip 压缩)

[
  // 配置第一个用户
  {
    // 浏览器用户代理
    userAgent: 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:102.0) Gecko/20100101 Firefox/102.0',
    // 云函数随机运行用的时间段
    dailyRunTime: '17:30:00-23:40:00',
    // 通用 api 延迟时间（s）
    apiDelay: [2, 6],
    // b 站 cookie （登录信息）可能需要双引号
    // prettier-ignore
    cookie: "xxxxx",
    // 配置运行的功能
    function: {
      // 瓜子兑换硬币
      silver2Coin: true,
      // 投币
      addCoins: true,
      // 直播签到
      liveSignTask: true,
      // 分享和观看
      shareAndWatch: true,
      // 漫画任务
      mangaTask: false,
      // 应援团签到
      supGroupSign: false,
      // 充电
      charging: false,
      // 获取 vip 权益
      getVipPrivilege: true,
      // 直播赠送礼物
      giveGift: false,
      // 赛事竞猜
      matchGame: false,
      // 直播天选时刻
      liveLottery: false,
      // 粉丝牌等级
      liveIntimacy: false,
      // 大会员大积分
      bigPoint: false,
    },
    // 消息推送
    message: {
      // 换行
      br: '\n',
      // 邮箱
      email: {
        from: '',
        to: '',
        pass: '',
        host: 'smtp.163.com',
        part: 465,
      },
      // push+
      pushplusToken: '',
      // server 酱
      SCKEY: '',
      // ... 更多省略
      // 自定义
      api: '',
    },
    // 投币相关
    coin: {
      // 目标等级
      targetLevel: 6,
      // 保留的硬币数
      stayCoins: 0,
      // 投币的数量（上限5）
      targetCoins: 5,
      // 自定义 up
      customizeUp: [],
      // 当获取已投币数量失败，假设已投币数量
      todayCoins: 0,
      // 是否只投指定 up
      upperAccMatch: true,
    },
    // 充电
    charge: {
      // 对象，默认自己
      // mid: 0,
      /** 充电预设时间，哪一天？ */
      presetTime: [10, 20],
    },
    // 赛事竞猜
    match: {
      // 每次竞猜的数量
      coins: 5,
      // 压赔率低的（正压）大于 0 的数，反之等于 0
      selection: 1,
      // 赔率需要达到的差距
      diff: 0.0,
    },
    // 天选时刻
    lottery: {
      // 奖品描述不能包含，比如“自拍一张”将被跳过
      excludeAward: [
        '舰',
        '船',
        '航海',
        '代金券',
        '优惠券',
        '自拍',
        '照',
        '写真',
        '图',
        '提督',
        '车车一局',
        '再来一局',
        '游戏道具',
      ],
      // 奖品描述包含，如果满足则跳过 excludeAward
      includeAward: ['谢'],
      // up 黑名单（up 的 id，不是房间号）
      blackUid: [65566781, 1277481241, 1643654862, 603676925],
      /** 是否将天选时刻关注 UP 移动到分组 */
      isMoveTag: true,
      // 关注的用户统一移动到此分组
      moveTag: '天选时刻',
      // 扫描几页直播间
      pageNum: 2,
      /** 关注回复处理方式  */
      actFollowMsg: 'read',
      /** 扫描关注的用户 */
      scanFollow: '',
      /** 跳过需要关注的天选 */
      skipNeedFollow: false,
    },
    // 直播间礼物
    gift: {
      // 自定义投喂礼物 UP， 在所填中随机选取
      mids: [],
    },
    // 亲密度
    intimacy: {
      // 直播弹幕
      liveSendMessage: true,
      // 分享直播间
      liveShare: true,
      // 点赞直播间
      liveLike: true,
      // 30 分钟直播心跳（默认关闭）
      liveHeart: false,
      // 白名单
      whiteList: [],
      // 黑名单
      blackList: [],
    },
    // 漫画
    manga: {
      // 签到
      sign: true,
      // 购买漫画
      buy: false,
      // 购买漫画 id（优先级高）
      mc: [],
      // 购买漫画名称（优先级中）
      name: [],
      // 购买追漫（优先级低）
      love: true,
      // 执行购买漫画间隔时间（单位天）
      buyInterval: 6,
      // 星期几执行购买漫画
      buyWeek: [3],
    },
  },
  // 配置第二个用户，和上面一样的配置，
  {
    // cookie: "xxxxxxxxxx"
  },
]
