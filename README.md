# 📏 Rebar Splice Length Reference APP
[English](#english) | [中文](#中文-1)

---

## English

A lightweight, offline-capable Progressive Web App (PWA) designed specifically for Rebar Detailers and Quantity Surveyors (QS) in the construction industry. It provides instant, accurate calculations for Tension Anchorage Lengths (T.A.L.) and Tension Lap Lengths (T.L.L.) without the need to manually cross-reference complex engineering tables.

### ✨ Core Features

* **Instant Calculation:** Simultaneously displays T.A.L., T.L.L. (Good Bond), and T.L.L. (Poor Bond) based on selected parameters.
* **Comprehensive Data Coverage:** Built-in standard reference tables covering:
    * **6 Concrete Grades (fck):** C25/30, C28/35, C32/40, C35/45, C40/50, C50/60
    * **8 Bar Diameters (Φ):** 10mm, 12mm, 16mm, 20mm, 25mm, 32mm, 40mm, 50mm
    * **3 Lap Proportions (α6):** BASIC REQUIRED, 50% LAP ON ONE LOCATION, 100% LAP ON ONE LOCATION.
* **Engineering Rounding Rule:** All final calculated lengths automatically round up to the nearest 10mm (e.g., any non-zero ones digit rounds up to the next ten: 1974mm becomes 1980mm) to strictly meet practical site cutting and detailing standards.
* **PWA Ready:** Can be installed directly to the home screen of any mobile device (Android/iOS) as a standalone application. Functions 100% offline via Service Worker caching.
* **Optimized UI/UX:** Uses large, touch-friendly "pill" buttons instead of native radio dots for faster, error-free data entry on mobile screens.

### 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3, Vanilla JavaScript (No heavy frameworks, ensuring lightning-fast load times).
* **PWA Integration:** `manifest.json` and `sw.js` (Service Worker) for offline availability and native-app-like installation.
* **Deployment:** Automated CI/CD via [Cloudflare Pages](https://pages.cloudflare.com/).

### 📱 Installation Guide

This web app behaves like a native mobile application. To install it on your device:

**For Android (Chrome / Samsung Internet):**
1. Open the application URL in your mobile browser.
2. Tap the browser menu (three dots `⋮` or `≡`).
3. Select **"Install app"** or **"Add to Home screen"**.
4. The app will be installed and appear in your app drawer with a dedicated icon, running in full-screen mode without browser UI.

### ⚙️ Logic & Formulas

The application derives final lengths by cross-referencing the base matrix arrays and applying the following multipliers:
* **T.A.L.:** `Base Value * 0.7`
* **T.L.L. (Good Bond):** Multiplied by `0.7` (BASIC REQUIRED), `0.98` (50% LAP), or `1.05` (100% LAP).
* **T.L.L. (Poor Bond):** Extracts direct table values for Basic, 50%, and 100% lap conditions.

*Note: All floating-point results undergo a custom `Math.ceil(num / 10) * 10` function before rendering.*

---

## 中文(钢筋驳接长度查表 APP)

专为建筑行业钢筋拆图师（Rebar Detailer）与工料测量师（QS）量身打造的轻量化、支持离线使用的渐进式 Web 应用（PWA）。本应用提供受拉锚固长度（T.A.L.）与受拉搭接长度（T.L.L.）的即时、精准查询与计算，无需再繁琐地手动翻阅复杂工程图表。

### ✨ 核心功能

* **同步即时计算：** 只需一键选择参数，即可在同一界面同时输出 T.A.L.、T.L.L.（良好粘结）和 T.L.L.（较差粘结）三个核心数值。
* **完整标准数据内置：** 完整录入了标准图表中的所有基础数据，涵盖：
    * **6 种混凝土强度 (fck)：** C25/30, C28/35, C32/40, C35/45, C40/50, C50/60
    * **8 种钢筋直径 (Φ)：** 10mm, 12mm, 16mm, 20mm, 25mm, 32mm, 40mm, 50mm
    * **3 种搭接比例 (α6)：** BASIC REQUIRED（基础版）, 50% LAP ON ONE LOCATION（进阶版 50%）, 100% LAP ON ONE LOCATION（进阶版 100%）。
* **工程专属进位规则：** 所有最终计算出的长度均自动**向上取整至最近的 10mm 倍数**（例如：个位数只要不是 0，一律向十位进 1，如 1974mm 自动变为 1980mm），严格符合工地现场实际下料、切配与拆图标准。
* **完美支持 PWA 安装：** 可直接作为独立应用程序安装到各类移动设备（安卓三星/苹果 iOS）的主屏幕与应用抽屉中。通过 Service Worker 缓存机制，支持 100% 离线使用。
* **极致优化的操作交互：** 弃用了原生微小的单选框圆点，全面采用大面积、易触控的“块状按键（Pill Buttons）”排版，极大地提高了手机端高频盲操时的录入速度，杜绝误触。

### 🛠️ 技术栈

* **前端技术：** HTML5, CSS3, 原生 JavaScript（无任何重型框架依赖，确保毫秒级极速启动）。
* **PWA 支持：** 包含 `manifest.json` 与 `sw.js`（服务工作线程），实现离线可用与原生应用级安装特性。
* **自动化部署：** 通过 [Cloudflare Pages](https://pages.cloudflare.com/) 实现与 GitHub 仓库的自动流水线（CI/CD）托管部署。

### 📱 手机端安装指南

本 Web 应用的运行效果与原生手机 App 完全一致。安装方法如下：

**安卓端（Chrome 浏览器 / 三星自带浏览器）：**
1. 在手机浏览器中打开部署好的网址。
2. 点击浏览器右上角的菜单图标（三个点 `⋮` 或 三条杠 `≡`）。
3. 在列表中找到并点击 **“安装应用” (Install app)** 或 **“添加到主屏幕”**。
4. 应用将完成安装并生成独立的图标出现在你的手机桌面和**应用抽屉**中，全屏沉浸式运行，不再显示浏览器地址栏。

### ⚙️ 计算逻辑与公式

应用通过检索后台内置的代码矩阵提取基准值（Base Value），并应用以下系数进行计算：
* **T.A.L.：** `基准值 * 0.7`
* **T.L.L. (良好粘结 / Good Bond)：** 分别乘以 `0.7`（BASIC REQUIRED）, `0.98`（50% LAP）, 或 `1.05`（100% LAP）。
* **T.L.L. (较差粘结 / Poor Bond)：** 直接提取对应表格（Basic、50%、100%）在较差条件下的固有数值。

*注：所有计算出的浮点数结果在渲染到界面前，均会通过自定义的 `Math.ceil(num / 10) * 10` 函数进行强行进位处理。*
