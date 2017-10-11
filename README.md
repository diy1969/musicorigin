# [个人音乐网站（木汐音乐）](http://39.108.72.180:8081)
**本网站属于个人作品展示，所有技术具有高度实验性质**

## 网站兼容性，暂考虑chrome、firefox、safari三端（完全不考虑IE）
> 1. Chrome 完全兼容
> 2. Firefox 对歌曲下载暂不兼容，但是后续考虑在firefox下补全下载功能
> 3. Safari 因为webaudioapi的差异性，导致无法兼容歌曲分段传输，所以可能会导致歌曲一开始播放不了

## 本网站所用技术
> 1. Vue 以及配套技术链
> 2. nodeJs 实现后台用户管理，抓取音频资源，以及实现音频资源分段加载
> 3. mongodb 数据库，实现用户信息存储
> 4. webaudioApi 实现音频相关操作，可视化数据处理
> 5. 其余的功能需求，自己手写。。。

## 源码介绍
### 前端项目主要代码 src 目录
> 1. 业务代码主要存放于 src/components
> 2. 功能需求实现主要存放于 src/common
### node项目主要代码 node 目录
> 1. 本地用户信息，音频分段加载等相关代码主要存放于 node/selfRouter
> 2. 网易云信息获取代码主要存放于 node/router [(相关api文档来自这里)](https://binaryify.github.io/NeteaseCloudMusicApi)
> 3. 所用的技术细节，可以加Q详细谈：996955311

## 网站功能介绍
### 音乐控件
> 1. 歌曲头像，点击进入歌曲详情页面，必须有歌曲播放才能进入
> 2. 切换歌曲，为了避免歌曲混乱，时间限制为2s
> 3. 歌曲快进，必须等歌曲片段加载并解码完成才能播放，若是加载还未解码时，不能快进
> 4. 当前播放歌曲列表栏，提供歌曲收藏，删除于当前播放列表的功能，双击歌曲播放
> 5. 均衡器按钮，提供不同的歌曲音质选择
> 6. 缩小按钮，使控件以缩小模式展示
> 7. 缩小控件提供的功能与主控件提供的功能基本一致

### 左边栏
> 1. 点击个人头像可以进行头像上传
> 2. 点击昵称可以进行昵称更改
> 3. 登录后在本网站停留一分钟增加一点经验

### 导航栏
> 1. 搜索按钮，输入音乐名称，得到搜索结果，默认显示30条数据，点击**加载更多**加载更多数据（暂只支持歌曲搜索，后续考虑实现歌单、歌手、专辑搜索）
> 2. 登录按钮，点击弹出登录注册页面，左边为登录界面，右边为注册界面
> 3. 主题切换按钮，点击弹出主题切换界面，分为主题和纯色两类，功能实现为手动切换和自动切换，当手动选择一个主题时，默认退出自动切换模式
> 4. 精简按钮，功能暂未实现（以后有时间会补上）
> 5. 可视化窗口按钮，进入音乐可视化界面，自我感觉还是挺好看的，可视化窗口分为可视化界面和歌词界面，因时间所限，歌词窗口暂未实现

### 发现音乐
> 1. 个性推荐，轮播图，推荐歌单（点击进入歌单详情页面），推荐新音乐，推荐电台
> 2. 歌单，可以查看各种类型的歌单，页面展示默认做了分页处理
> 3. 排行榜，查看各种榜单，默认显示六个榜单，点击**加载更多**显示更多的榜单

### 下载音乐
> 1. 正在下载，下载功能为队列下载，歌单下载或多首歌曲下载，实现为队列操作，下载完成后自动添加到当前用户的下载列表中
> 2. 已下载，展示当前用户已经下载过的歌曲信息，双击歌曲可播放

### 我的音乐
> 1. 展示当前用户收藏的歌曲信息，双击歌曲可播放

### 收藏的歌单
> 1. 展示当前用户的收藏歌单信息，点击进入歌单详情页面

### 歌单详情页面
> 1. 歌曲列表展示，提供收藏，下载功能，双击可播放歌曲
> 2. 云音乐评论可以查看当前歌单在网易云音乐中的评论
> 3. 本地评论，可以对当前歌单进行评论，也可以对某条评论进行回复
> 4. 云音乐评论和本地音乐评论统一默认做分页处理，默认加载评论数量为20条，点击**加载更多**可以获得更多的评论

### 当前播放歌曲详情页面
> 1. 歌词展示页面，纯歌词展示，界面效果感觉还是蛮舒服的，点击当前页面回到主页面
> 2. 鼠标下滑翻转到歌曲评论，相似音乐页面
> 3. 歌曲评论页面功能与歌单评论页面功能基本一致
