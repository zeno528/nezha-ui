# 免费随机背景图接口（实测可用）

> 2026-08-12 实测，国内网络环境可直接访问。免费接口随时可能失效，失效就换下一个；重要场合建议用自己图床的固定图片直链。

## 用法

把接口 URL 填进面板 **自定义代码（样式和脚本）** 的 `window.CustomBackgroundImage`：

```javascript
window.CustomBackgroundImage = "https://api.imlcd.cn/bg/high.php?return=img";
window.CustomMobileBackgroundImage = "https://api.imlcd.cn/bg/high.php?return=img";
```

保存后刷新页面生效。

## 必应每日壁纸（自动更新，推荐）

| 接口 | 大小 | 速度 |
|:---|:---|:---|
| `https://api.imlcd.cn/bg/high.php?return=img` | 339KB | 0.6s |
| `https://api.eyabc.cn/api/background/bing` | 339KB | 1.2s |

## 动漫风

| 接口 | 大小 | 速度 |
|:---|:---|:---|
| `https://uapis.cn/api/v1/random/image?category=acg&type=pc` | 1MB | 0.1s（最快） |
| `https://api.fuchenboke.cn/api/dongman.php` | 257KB | 0.4s（最轻） |
| `https://img.paulzzh.com/touhou/random?size=pc` | 211KB | 0.5s（东方 Project） |
| `https://www.loliapi.com/acg/pc/` | 1.6MB | 0.4s |
| `https://api.imlcd.cn/bg/acg.php?return=img` | 1.3MB | 3.3s（偏慢） |
| `https://wp.upx8.com/api.php?category=anime&resolution=1920x1080` | 1.7MB | 0.3s |
| `https://api.eyabc.cn/api/picture/dong_man` | 900KB | 1.9s |

## 风景

| 接口 | 大小 | 速度 |
|:---|:---|:---|
| `https://api.imlcd.cn/bg/gq.php?return=img` | 474KB | 0.8s |
| `https://api.fuchenboke.cn/api/fengjing.php` | 101KB | 2.4s |
| `https://wp.upx8.com/api.php?category=nature&resolution=1920x1080` | 1MB | 0.4s |
| `https://picsum.photos/1920/1080` | 50KB | 0.7s（最轻） |
| `https://api.eyabc.cn/api/picture/scenery` | 788KB | 1.6s |

## 已失效（不要再用）

- `https://bing.img.run/rand_uhd.php`（原模板默认，已挂）
- `https://bing.img.run/rand_m.php`（已挂）
- `https://img.xjh.me/random_img.php?type=bg&ctype=acg&return=302`（502）
- `https://api.dujin.org/bing/1366.php`（521）
- `https://api.btstu.cn/sjbz/api.php?lx=dongman&format=images`（连接失败）
