---
name: cinematic-landing-page
description: 製作「科技旗艦品牌」風格的產品形象網站（類似 Apple、Tesla、SpaceX 的大圖、全版面、捲動敘事風格）。當使用者要做產品介紹頁、形象官網、landing page，或說「做一個像 Apple / Tesla / SpaceX 那樣的網站」時使用。輸出為單一 HTML 檔，附教學用中文註解。
---

# Cinematic Landing Page（旗艦科技品牌風格網站）

這份 skill 用來教學：讓學生學會「頂級科技品牌官網」背後的**設計原則與前端技巧**，
做出**自己原創品牌**的網站。我們學的是「風格與手法」，不是複製別人的網站。

---

## 0. 著作權與商標規則（一定要遵守）

- **絕對不要**使用 Apple、Tesla、SpaceX 或任何真實公司的名稱、Logo、商標、產品名、
  官網文案或圖片。網站必須是**虛構或學生自己的品牌**。
- 如果學生要求「做一個 Apple 官網」，就說明：我們學它的風格，但品牌換成原創的，
  並請學生取一個品牌名（或由你提議 2–3 個虛構名稱讓他選）。
- 圖片只用：學生自己提供的圖片、CSS 漸層、SVG 原創圖形，或明確標示授權的素材。
  不要從網路下載真實產品照或名人照片。
- 頁尾不要放假的公司地址、統編、認證標章等會讓人誤以為是真公司的資訊；
  加一行小字：「本網站為課堂練習作品，品牌為虛構」。

---

## 1. 開始前先問學生（最多 3 題）

1. **品牌與產品**：你的品牌叫什麼？賣什麼？（例：智慧手錶、電動機車、火箭發射服務、實驗室儀器）
2. **風格**：選一種，或混合：
   - **A. 極簡產品風**（Apple 式）
   - **B. 全螢幕沉浸風**（Tesla 式）
   - **C. 太空任務風**（SpaceX 式）
3. **素材**：有沒有自己的照片？沒有的話，就用 CSS 漸層與 SVG 製作視覺。

若學生沒回答，就自己選最合理的組合，並在開頭說明你的假設。

---

## 2. 三種風格的設計語言

### A. 極簡產品風（Apple 式）
| 元素 | 規則 |
|---|---|
| 色彩 | 大面積純白 `#fff` 或近黑 `#000`/`#1d1d1f`；強調色只用一個（常見藍色連結 `#0071e3`） |
| 字體 | 系統無襯線字：`-apple-system, "SF Pro Display", "Helvetica Neue", "Noto Sans TC", sans-serif`；標題極大（`clamp(48px, 8vw, 96px)`）、字重 600、字距略緊 `letter-spacing: -0.02em` |
| 排版 | 置中對齊；每一屏只講**一件事**；大量留白 |
| 敘事 | 「標題 → 一句副標 → 兩個文字連結（了解更多 › / 購買 ›）→ 大產品圖」 |
| 動態 | 捲動時元素淡入上移；**sticky 捲動敘事**（畫面固定、文字隨捲動切換）；數字或規格逐一出現 |
| 其他 | 規格比較用卡片網格（圓角 18–28px、淺灰底 `#f5f5f7`） |

### B. 全螢幕沉浸風（Tesla 式）
| 元素 | 規則 |
|---|---|
| 版面 | 每個 section 都是 `100vh` 全螢幕，用 `scroll-snap` 一屏一屏切換 |
| 背景 | 滿版大圖或影片，文字直接壓在圖上 |
| 文字 | 標題在上方 1/4 處置中；副標小字；文字色依背景切換黑/白 |
| 按鈕 | 底部兩顆並排膠囊按鈕：一顆實心深色（主要）、一顆半透明淺色（次要），寬度約 260px |
| 導覽列 | 透明、置頂、極簡；選單文字小、字重 500，hover 出現淡灰圓角底 |
| 動態 | 很少；靠「一屏一屏切換」本身產生節奏感 |

### C. 太空任務風（SpaceX 式）
| 元素 | 規則 |
|---|---|
| 色彩 | 全黑底 `#000`，白字，幾乎沒有其他顏色 |
| 字體 | **全大寫**、字距加寬 `letter-spacing: 0.1–0.2em`；可用 `"D-DIN", "Barlow", "Rajdhani"`（Google Fonts）營造工程感 |
| 版面 | 滿版暗色大圖，文字靠**左下**；細線框按鈕（1–2px 白框、hover 變白底黑字） |
| 敘事 | 「任務名稱 / 日期」小字 → 大標題 → 「WATCH」「LEARN MORE」按鈕 |
| 數據 | 大數字統計列：`250+ LAUNCHES` 這種「大數字 + 小標籤」，可做計數動畫 |
| 動態 | 緩慢的背景縮放（Ken Burns 效果）、數字跳動、細線條進場 |

---

## 3. 技術規格

- **單一 HTML 檔**：HTML + `<style>` + `<script>` 全部寫在一起，雙擊就能開。不要用 React 或建置工具（教學目的：讓學生看得懂每一行）。
- 只用原生 HTML / CSS / JavaScript。字體可從 Google Fonts 載入。
- **響應式**：手機寬度（375px）必須正常顯示、沒有橫向捲軸；導覽列在手機改為漢堡選單。
- **無障礙**：圖片要有 `alt`；按鈕用 `<a>` 或 `<button>`；文字與背景對比足夠；
  所有動畫要包在 `@media (prefers-reduced-motion: no-preference)` 裡。
- **語意標籤**：`<header> <nav> <main> <section> <footer>`。
- **教學註解**：每個區塊前用中文註解說明「這段在做什麼、為什麼這樣做」，
  重要的 CSS 屬性旁邊也加一行短註解。

---

## 4. 必學的核心技巧（依風格挑用）

### 4.1 捲動淡入（三種風格都適用）
```html
<style>
  /* 初始狀態：透明、往下偏移 */
  .reveal { opacity: 0; transform: translateY(40px); transition: opacity .8s ease, transform .8s ease; }
  /* 進入畫面後加上 .show */
  .reveal.show { opacity: 1; transform: none; }
  @media (prefers-reduced-motion: reduce) { .reveal { opacity: 1; transform: none; transition: none; } }
</style>
<script>
  // IntersectionObserver：元素進入畫面 15% 時觸發，比監聽 scroll 事件更省效能
  const io = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('show'); io.unobserve(e.target); } });
  }, { threshold: 0.15 });
  document.querySelectorAll('.reveal').forEach(el => io.observe(el));
</script>
```

### 4.2 一屏一屏切換（Tesla 式）
```css
/* 外層容器負責捲動，子 section 對齊到頂端 */
html { scroll-snap-type: y mandatory; }
section.panel { height: 100vh; height: 100svh; scroll-snap-align: start; position: relative; }
```

### 4.3 Sticky 捲動敘事（Apple 式）
```css
/* 外層很高（例如 300vh），內層 sticky 固定在畫面上，
   JS 依捲動進度切換文字或放大圖片 */
.story { height: 300vh; position: relative; }
.story .stage { position: sticky; top: 0; height: 100vh; display: grid; place-items: center; }
```
```js
// 計算捲動進度 0 → 1，用來控制縮放、透明度或切換第幾段文字
const story = document.querySelector('.story');
addEventListener('scroll', () => {
  const r = story.getBoundingClientRect();
  const p = Math.min(1, Math.max(0, -r.top / (r.height - innerHeight)));
  story.style.setProperty('--p', p);   // CSS 用 calc(var(--p) * ...) 取用
}, { passive: true });
```

### 4.4 大數字計數動畫（SpaceX 式）
```js
// 數字從 0 跑到 data-target，進入畫面時才開始
function countUp(el) {
  const target = +el.dataset.target, dur = 1500, t0 = performance.now();
  const tick = now => {
    const k = Math.min(1, (now - t0) / dur);
    el.textContent = Math.floor(target * (1 - Math.pow(1 - k, 3))); // ease-out
    if (k < 1) requestAnimationFrame(tick);
  };
  requestAnimationFrame(tick);
}
```

### 4.5 沒有照片時的「產品視覺」
- 用 `radial-gradient` + `linear-gradient` 疊出光暈與金屬感背景。
- 用 SVG 畫簡單的原創產品輪廓（圓角矩形手錶、流線車身剪影、火箭剪影），
  加上 `filter: drop-shadow()` 增加立體感。
- 範例：`background: radial-gradient(circle at 50% 30%, #3a3f55, #000 70%);`

### 4.6 透明 → 實心導覽列
```js
// 捲動超過 50px 後，導覽列加上毛玻璃背景
const nav = document.querySelector('nav');
addEventListener('scroll', () => nav.classList.toggle('scrolled', scrollY > 50), { passive: true });
```
```css
nav.scrolled { background: rgba(255,255,255,.72); backdrop-filter: saturate(180%) blur(20px); }
```

---

## 5. 建議的頁面結構

1. **導覽列**：品牌名（文字 Logo）＋ 4–6 個選單項目
2. **Hero 首屏**：產品名 + 一句話標語 + 主次兩個 CTA
3. **2–4 個特色區塊**：每屏一個賣點（依風格用全屏、sticky 敘事或左下文字）
4. **規格 / 數據區**：卡片網格或大數字統計列
5. **最後號召**：「立即預訂」「加入任務」等收尾 CTA
6. **頁尾**：簡單連結 + 「本網站為課堂練習作品，品牌為虛構」

---

## 6. 交付前自我檢查清單

- [ ] 沒有出現任何真實公司的名稱、Logo、產品名或文案
- [ ] 單一 HTML 檔，瀏覽器直接開啟可運作，Console 沒有錯誤
- [ ] 手機寬度 375px 正常、無橫向捲軸
- [ ] 每屏只有一個重點訊息，留白充足
- [ ] 字級層次清楚：大標 / 副標 / 內文至少三層
- [ ] 動畫流暢，且有 `prefers-reduced-motion` 處理
- [ ] 每個區塊都有中文教學註解
- [ ] 交付時附 3–5 行說明：用了哪種風格、哪些核心技巧，以及學生可以自己動手改的地方（換顏色、換文案、加一個 section）

---

## 7. 給學生的延伸練習（交付時挑 2–3 個附上）

1. 把強調色換掉，觀察整體氣質怎麼改變。
2. 把 Tesla 式全屏切換改成一般捲動，比較體驗差異。
3. 新增一個 sticky 敘事區塊，讓產品圖隨捲動放大。
4. 加上深色模式（`prefers-color-scheme: dark`）。
5. 把網站部署到 GitHub Pages，取得公開網址。