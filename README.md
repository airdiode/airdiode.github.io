# airdiode — 总主页

GitHub Pages 的用户站点，对应 <https://airdiode.github.io/>。
仓库名必须是 `airdiode.github.io`，Pages 才会挂在根域名上。

主页只做一件事：**罗列产品**，不写总结也不写分析。

- 题头：一句「欢迎来到 JIANG HUI 的产品集」，下面两个入口——GitHub 与个人官网 godar.cn
- 产品：三行清单（`.product-list`），每行是图标 + 名称 + 一句说明 + 箭头
- 页脚：一行版权与链接

| 产品 | 站点 |
|---|---|
| 孤云 Guyun | `/Guyun/`（仓库 `airdiode/Guyun`） |
| 风雨如磐 | `/Fengyu/`（仓库 `airdiode/Fengyu`） |
| Quileg STM32 | `/Quileg-STM32/`（仓库 `airdiode/Quileg-STM32`） |

加一个产品：在 `<ul class="product-list">` 里复制一个 `<li>`，填名称、一句说明和链接即可；
不用动 hero 与页脚（页脚只有版权和两个外链）。

## 文件

```
index.html        中文主页（默认，挂在根域名）
en/index.html     英文主页，同一套版式与样式
styles.css        全部样式，含深色模式、产品清单与页脚
assets/mark.svg   站点标记（青绿两方块）与 favicon
assets/og.png     中文分享卡片图 1200×630
assets/og-en.png  英文分享卡片图
assets/guyun-icon.png   孤云的应用图标
assets/fengyu-mark.svg  风雨如磐的标志
assets/quileg-stm32.svg Quileg STM32 的图标
og.html           og.png 的源文件，用浏览器截图得到，不对外链接
og-en.html        og-en.png 的源文件
```

中英两页是**两份独立 HTML**（不用 JS 切语言），靠 `<link rel="alternate" hreflang>` 互相标注，
页头右上角各有一次互链：中文页 `en/`，英文页 `../`。改文案时两页都要改。

## 改内容

- 文案、链接：改 `index.html` 与 `en/index.html`
- 颜色：`styles.css` 顶部 `:root`；品牌色 `--guyun`，另两件用 `.card-fengyu` / `.card-stm32` 的 `--accent`
- 加一件作品：复制一张 `article.card.card-wide`，给它一个 `--accent`，再补关于、页脚、JSON-LD 与分享图
- 换图标：覆盖 `assets/guyun-icon.png`
- 分享图要重出时：

```bash
CHROME="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
"$CHROME" --headless=new --no-sandbox --disable-gpu --hide-scrollbars \
  --window-size=1200,630 --force-device-scale-factor=1 \
  --screenshot="assets/og.png" "file://$PWD/og.html"
# 英文版换 og-en.html / assets/og-en.png
```

## 发布

```bash
git add -A && git commit -m "home: …" && git push origin main
```

Pages 会在 30–60 秒内重建。

## 注意

- **这个仓库的 git 历史是重建过的**（旧仓库连同历史一起删了）。现在这条历史里不含任何旧项目内容；
  以后别把旧文件再提交进来，否则会重新出现在公开历史里。
- 页面上的外链都指向 `airdiode.github.io`；换用户名或换域名时记得全局替换。
