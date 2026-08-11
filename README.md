# nezha-ui

Fork 自 [ziwiwiz/nezha-ui](https://github.com/ziwiwiz/nezha-ui)，基于个人使用习惯做了调整。

## 与原版的区别

- `traffic-progress.js` 已跟进上游 `v20260803` 重构版（性能优化、防重复注入），并在其上沿用自定义颜色阈值：60%/90%，0~60% 绿色系渐变，60%~90% 转红，90% 以上深红。

## 怎么用（先看这里）

脚本分两类，粘贴位置不同：

| 粘贴位置 | 生效范围 |
|:---------|:---------|
| **自定义代码（样式和脚本）** | 整个面板所有页面 |
| **仪表板的自定义代码** | 仅首页（dashboard） |

位置：后台 **系统设置 → 自定义代码（样式和脚本）** / **仪表板的自定义代码**。

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/docs/traffic-script-setup.jpg"
       alt="哪吒面板自定义代码添加位置"
       width="75%"
       style="border: 2px solid #d0d7de; border-radius: 8px;">
  <br>
  <em>↑ 在面板这里填入下面的代码</em>
</p>

最基础的用法（只显示流量进度条），在 **自定义代码（样式和脚本）** 里粘贴：

```html
<script>
window.ShowNetTransfer=true;
</script>
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/traffic-progress.js"></script>
```

## 脚本总览

| 文件 | 作用 | 粘贴位置 |
|:-----|:-----|:---------|
| `traffic-progress.js` | 服务器卡片下方显示周期性流量进度条（用量/总量/百分比/周期日期） | 自定义代码（样式和脚本） |
| `nezha-style.css` | 探针页面美化（毛玻璃卡片、自定义背景图、边框阴影） | 自定义代码（样式和脚本） |
| `netstatus-autoshow.js` | 详情页直接展示网络波动图表，不用手动点"网络"Tab | 自定义代码（样式和脚本） |
| `nezha-time.css` | 首页时间改为大号发光数字时钟 | 自定义代码（样式和脚本） |
| `nezha-dashboard.js` | 首页美化：自定义左上角标题、禁用动画、MiSans 字体 | 仪表板的自定义代码 |
| `nezha-dashboard.css` | 配合上方脚本的样式（字体、隐藏页脚） | 仪表板的自定义代码 |
| `nezha-itdog.js` | 服务器 IP 旁加 Ping / TCPing 按钮（修复 IPv4:port 误判 IPv6） | 仪表板的自定义代码 |

## 使用方式

###### 1. 后台基础美化（nezha-style.css + 探针变量）
在 **自定义代码（样式和脚本）** 中粘贴：

```html
<meta name="referrer" content="no-referrer">
/* 自用的css格式 */
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-style.css">
/* 自用的探针修改 */
<script>
    window.CustomBackgroundImage = "https://bing.img.run/rand_uhd.php"; /* 页面背景图 */
    window.CustomMobileBackgroundImage = "https://bing.img.run/rand_m.php"; /* 移动端页面背景图 */
    /* 卡片显示上下行流量 */
    // window.ShowNetTransfer = "true";
    /* 关掉人物插图 */
    window.DisableAnimatedMan = "true";
    /* 自定义描述 */
    window.CustomDesc = "v2.games";
</script>
```

可配置项：

| 变量 | 作用 |
|:-----|:-----|
| `CustomBackgroundImage` | 桌面端背景图 URL |
| `CustomMobileBackgroundImage` | 移动端背景图 URL |
| `ShowNetTransfer` | 设为 `"true"` 时卡片显示上下行流量 |
| `DisableAnimatedMan` | 设为 `"true"` 时关闭人物插图 |
| `CustomDesc` | 自定义描述文字 |

###### 2. 周期性流量进度条（新版 v20260803，推荐）
在 **自定义代码（样式和脚本）** 中粘贴：

```html
<script>
window.ShowNetTransfer=true;
</script>
<script>
  window.TrafficScriptConfig = {
    showTrafficStats: true,    // 显示流量统计
    insertAfter: true,         // 如果开启总流量卡片, 放置在总流量卡片后面
    interval: 60000,           // 60秒刷新缓存, 单位毫秒
    toggleInterval: 4000,      // 4秒切换流量进度条右上角内容, 0秒不切换, 单位毫秒
    duration: 500,             // 缓进缓出切换时间, 单位毫秒
    enableLog: false           // 开启日志
  };
</script>
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/traffic-progress.js"></script>
```

###### 3. 详情页直接展示网络波动卡片
在 **自定义代码（样式和脚本）** 中粘贴（无需配置，自动生效）：

```html
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/netstatus-autoshow.js"></script>
```

效果：点进服务器详情页时，直接同时展示"详情"和"网络"两个图表，不用再手动点"网络"Tab。

###### 4. 页面时间修改（大号数字时钟）
在 **自定义代码（样式和脚本）** 中粘贴（无需配置，自动生效）：

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-time.css">
```

效果：首页时间改为大号发光数字时钟，隐藏"当前时间"文字。

###### 5. 仪表板的自定义代码（首页美化 + IP 测速按钮）
在 **仪表板的自定义代码** 中粘贴：

```html
<!-- 首页美化：左上角标题、禁用动画、MiSans 字体 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-dashboard.css">
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-dashboard.js"></script>

<!-- 服务器 IP 旁显示 Ping / TCPing 按钮 -->
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-itdog.js"></script>
```

如需修改左上角标题，在引用前加配置：

```html
<script>
  const neZhaConfig = {
    disableAnimatedMan: true,   // 是否禁用动画
    adminTitle: 'v2.games',     // 左上角后台名称
    fontUrl: 'https://font.sec.miui.com/font/css?family=MiSans:400,700:MiSans', // 自定义字体
    fontFamily: 'MiSans',       // 字体名称
  };
</script>
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-dashboard.js"></script>
```

## 常见问题

**流量进度条不显示？**
确认 `window.ShowNetTransfer=true;` 和脚本引用都粘贴在 **自定义代码（样式和脚本）** 里，且只加载了一个 traffic-progress 脚本。

**改了脚本没生效？**
jsdelivr 有缓存，等几分钟即可。若 `cdn.jsdelivr.net` 加载异常（如 DNS 污染），可换成 jsdelivr 的其他 CDN 端点（实测均可用）：

```html
<script src="https://fastly.jsdelivr.net/gh/zeno528/nezha-ui@main/traffic-progress.js"></script>
<!-- 或 -->
<script src="https://gcore.jsdelivr.net/gh/zeno528/nezha-ui@main/traffic-progress.js"></script>
```

## 致谢

- 原作者：[ziwiwiz](https://github.com/ziwiwiz/nezha-ui)
