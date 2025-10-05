# 使用 Selenium WebDriver 的 Bright Data 酒店搜索抓取器

本项目演示如何将 Bright Data 的 Scraping Browser 与 Selenium WebDriver 结合使用，在 Booking.com 上搜索酒店。它提供了一个通过自动化浏览器控制进行网页抓取的实用示例。

<a href="https://codesandbox.io/p/devbox/github/luminati-io/bright-data-scraping-browser-selenium-webdriver-project?file=%2Fbooking-hotel-scraping.js" target="_blank" rel="noopener">在 CodeSandbox 中打开</a>，使用 GitHub 账号登录，然后 fork 该仓库以开始修改。

### 开始使用

1. 在 `booking-hotel-scraping.js` 中将 `YOUR_BRIGHT_DATA_SCRAPING_BROWSER_ENDPOINT` 替换为你实际的 Bright Data 抓取浏览器端点
2. 运行 `node booking-hotel-scraping.js` 开始抓取

## 💻 使用方法

1. 在 `booking-hotel-scraping.js` 中修改搜索参数：
   ```javascript
   const SEARCH_LOCATION = "New York";  // 修改为你想要的地点
   const CHECK_IN_DAYS_FROM_NOW = 1;    // 调整入住日期
   const CHECK_OUT_DAYS_FROM_NOW = 2;   // 调整退房日期
   ```

2. 运行脚本：
   ```bash
   node booking-hotel-scraping.js
   ```

## 🔍 工作原理

脚本使用 Selenium WebDriver：
1. 连接到 Bright Data 的 Scraping Browser
2. 访问 Booking.com
3. 处理可能出现的弹窗
4. 填写地点与日期的搜索表单
5. 提交搜索并等待结果
6. 抽取酒店信息（名称、价格、评分）
7. 以表格形式展示结果

```javascript
// 使用 Bright Data 的 Scraping Browser 初始化 WebDriver
driver = await new Builder()
    .forBrowser(Browser.CHROME)
    .usingServer(SCRAPING_BROWSER)
    .build();
```

## 📊 示例输出

```
📊 搜索结果:
==================
┌─────────┬─────┬────────────────────┬──────────┬─────────┐
│ (index) │  #  │     Hotel Name     │  Price   │ Rating  │
├─────────┼─────┼────────────────────┼──────────┼─────────┤
│    0    │  1  │ Hotel Name 1       │ $100     │ 8.5     │
│    1    │  2  │ Hotel Name 2       │ $150     │ 9.0     │
│    2    │  3  │ Hotel Name 3       │ $200     │ 8.8     │
└─────────┴─────┴────────────────────┴──────────┴─────────┘
```
