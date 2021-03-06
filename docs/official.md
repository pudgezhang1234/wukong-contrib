# 悟空的官方插件

## Email

检查邮件功能。

### 触发条件

1. 用户已在 ~/.wukong/config.xml 中完成了邮箱的配置。
2. 指令中有关键词 “邮件” 。

语音播报的规则：
- 如果配置 `read_email_title` 选项为 `true`，会同时阅读邮件标题。如果为 `false`，则只阅读邮件的发件人信息。
- 如果邮件的标题带有 `[echo]` 的前缀，则不管 `read_email_title` 值为什么，都会阅读该邮件的标题，并且不会播报发件人信息（可利用该功能来实现传话、其他事件监控播报，例如与 ifttt 结合发布各类通知）。
- 如果邮件的标题带有 `[control]` 的前缀，且发件人是用户的邮箱，则将当成一条远程命令指令进行响应。

### 示例

- 用户：“我有多少封邮件？”
- 悟空：“您有一封来自 m at hahack.com 的未读邮件”

## Camera

用于调起摄像头拍照（如果安装了摄像头的话）。

### 适用平台

适用于树莓派或者带有USB摄像头的PC。

### 触发条件

指令中有关键词 “拍照” 或 “拍张照” 时。

如果接入了邮箱，照片将发送到用户的邮箱中。

### 示例

#### 倒计时拍照

- 用户：“拍张照”。
- 悟空：“收到，3秒后启动拍照……咔擦（拍照声）……拍照成功！正在发送照片到您的微信……发送成功！”

#### 无声拍照

- 用户：“偷偷地拍张照”（也可以使用微信发）。
- 悟空：“……（无声）”

### 配置

``` yml
# 拍照
camera:
    enable: true
    dest_path: "/home/pi/camera" # 保存目录
    quality: 5              # 成像质量（0~100）
    vertical_flip: false    # 竖直翻转
    horizontal_flip: false  # 水平翻转
    count_down: 3           # 倒计时（秒），仅当开启倒计时时有效
    sendToUser: true        # 拍完照是否发送到邮箱/微信
    sound: true             # 是否有拍照音效
    usb_camera: false              # 是否是 USB 摄像头
```

如果是 USB 摄像头，还需要确保安装了 fswebcam ：

``` sh
sudo apt-get install fswebcam
```

## CleanCache

用于清除 dingdang 运行时产生的所有临时数据（包括语音缓存数据）

### 触发条件

指令中有关键词 “清除缓存” 或 “清空缓存”

### 示例

- 用户：“清除缓存”
- 悟空：“缓存目录已清空”

## Poem

让 wukong-robot 给你写一首诗

### 触发条件

指令中有关键词 ”写诗“ 

### 示例

- 用户：”写一首关于大海的诗“
- 悟空：”神州大海起风浪,诗友词坛聚一堂,我自天涯歌盛世,君从塞外写华章“
- 用户：”写诗“
- 悟空：”曾写诗行几度秋,酸甜苦辣共登楼,谁言此地无春色,我自吟哦乐不休“
