# nezha-ui

Fork 自 [ziwiwiz/nezha-ui](https://github.com/ziwiwiz/nezha-ui)，基于个人使用习惯做了调整。

## 与原版的区别

### traffic-progress.js（周期性流量进度条）

调整了进度条颜色的百分比阈值：

| 百分比 | 颜色 | 说明 |
|:-------|:-----|:-----|
| 0%~60% | 🟢 绿 → 🟠 橙 | 正常使用范围 |
| 60%~90% | 🟠 橙 → 🔴 红 | 流量偏高提醒 |
| 90%~100% | 🔴 深红 | 流量即将耗尽 |

原版阈值为 35%/85%，对大部分 VPS 来说偏早变色，调整为 60%/90% 更合理。

## 使用方式

### 周期性流量进度条

在面板设置 → 自定义代码中添加：

```html
<script>
  window.ShowNetTransfer=true;
</script>
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/traffic-progress.js"></script>
```

可选配置项：

```html
<script>
  window.TrafficScriptConfig = {
    showTrafficStats: true,    // 显示流量统计
    insertAfter: true,         // 放置在总流量卡片后面
    interval: 60000,           // 60秒刷新缓存（毫秒）
    toggleInterval: 4000,      // 4秒切换右上角内容（毫秒）
    duration: 500,             // 切换动画时长（毫秒）
    enableLog: false           // 开启日志
  };
</script>
```

### 其他脚本

以下脚本未做修改，与原版一致：

```html
<!-- 自定义样式 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-style.css">

<!-- 网络波动卡片 -->
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/netstatus-autoshow.js"></script>

<!-- 仪表板自定义 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-dashboard.css">
<script src="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-dashboard.js"></script>

<!-- 页面时间样式 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zeno528/nezha-ui@main/nezha-time.css">
```

## 致谢

- 原作者：[ziwiwiz](https://github.com/ziwiwiz/nezha-ui)
