# NeekBOT 聊天报价系统 — 前端开发 PRD

> **版本**: v1.0  
> **原型文件**: `leadin/leadpquote.html`（在线预览：https://loisyuyou.github.io/v3.3neekbotdemo/leadpquote.html）  
> **技术栈**: Taro 4.x + Vue3 (Script Setup) + CSS Modules + NutUI + Pinia  

---

## 一、页面总览

本产品包含 **2 个主页面**（聊天页 + 报价单页）和 **5 个弹窗/抽屉**，共计 **7 个 UI 层级**。

| 序号 | 页面/组件 | 类型 | 触发方式 |
|------|----------|------|---------|
| 1 | 聊天主页 | 主页面 | 默认展示 |
| 2 | 报价单详情页 | 全屏覆盖页 | 点击「查看详细报价单」或「历史报价」卡片 |
| 3 | 参团二维码弹窗 | 居中弹窗 | 点击「立即参团」 |
| 4 | 专属顾问二维码弹窗 | 居中弹窗 | 点击「联系专属顾问」 |
| 5 | 报价单客服二维码弹窗 | 居中弹窗 | 报价单页点击「联系客服确认行程」 |
| 6 | 定制需求表单抽屉 | 底部抽屉 | 点击预算卡片的「定制xxx方案」 |
| 7 | 全部地接社列表抽屉 | 底部半屏抽屉 | 报价单页点击「全部」按钮 |

---

## 二、聊天主页（Page 1）

### 2.1 导航栏
- **标题**: "NeekBOT"
- **副标题**: "基于10000+真实行程训练生成"
- 固定顶部，不随内容滚动

### 2.2 消息区域
可纵向滚动，包含以下模块从上到下排列：

#### 2.2.1 Intro 卡片（品牌介绍卡）
- 顶部 eyebrow 文字："NEEKBOT"
- 三栏统计数据：
  - 10000+ 真实行程
  - 1000+ 服务客户
  - 10年 地接经验

#### 2.2.2 Quick Match 预算卡片轮播模块
- **模块标题**: "Quick Match"
- **模块描述**: "左右滑动看看不同预算下的非洲体验会是什么样的？"
- **轮播卡片列表**（7张，可左右滑动，snap 吸附）：

| 卡片 | 预算区间 | 卡片标签 | CTA 按钮文字 | CTA 行为 |
|------|---------|---------|------------|---------|
| 特种兵王 | $400-$1,500 | 无 | 立即参团 | 打开参团二维码弹窗 |
| 入门打卡 | $1,500-2,200 | 🥉12-15%选择 | 定制入门方案 | 打开定制表单抽屉 |
| 经典之选（高亮） | $2,200-2,800 | ⬆🥇 45-50%选择！ | 定制经典方案 | 打开定制表单抽屉 |
| 深度体验 | $2,800-3,500 | 🥈20-25%选择 | 定制深度方案 | 打开定制表单抽屉 |
| 小资轻奢 | $3,500-4,500 | 💎10-12%选择 | 定制轻奢方案 | 打开定制表单抽屉 |
| 奢华进阶（暗色主题） | $4,500-7,000 | 👑10-12%选择 | 定制奢华方案 | 打开定制表单抽屉 |
| 顶级定制（暗色主题） | $7,500+ | ⚜️ 稀有 | 联系专属顾问 | 打开专属顾问二维码弹窗 |

**每张卡片结构**：
1. **Hero 图片区**: 背景图 + 阶梯名 + 价格区间
2. **Body 区域**:
   - 一句话体验描述（如"舒适均衡 · 最高性价比"）
   - 四项参数指标：天数 / 人数 / 交通 / 住宿
   - 适合谁 vs 需接受（两栏对比）
   - CTA 按钮

**交互细节**：
- 页面加载后自动滚动到「经典之选」高亮卡片居中
- 鼠标拖拽滚动，松手后 snap 吸附
- 最多添加 **3 种对比方案**，已添加的方案 CTA 按钮置灰 disabled
- 特种兵王的「立即参团」→ 参团弹窗（不走定制流程）
- 顶级定制的「联系专属顾问」→ 顾问弹窗（不走定制流程）

#### 2.2.3 聊天气泡区域（#chatHistory）
- Bot 头像："N"
- 气泡中可包含：文字 + 「查看详细报价单」按钮
- 新消息自动滚动到底部

### 2.3 底部输入区（Composer）
- **左侧**: 出行档案书签区（动态生成，详见 2.4）
- **右侧**: 输入框 + 发送按钮
  - placeholder: "告诉 NeekBot 你的想法..."

### 2.4 出行档案书签（Profile Bookmark）
提交定制需求后，底部输入区上方出现可折叠的书签卡片。

**结构**：
1. **标签栏**: 横向排列已添加的方案标签（如"经典方案（均衡型）"），可切换
2. **折叠/展开按钮**: ▲ 箭头
3. **内容区**（展开时显示）：
   - 预算区间（大字展示）
   - 四格参数：目的地 / 出发日期 / 出行人数 / 游玩天数
   - 日期和人数、天数**可点击编辑**（contenteditable / date input），编辑后自动生成新报价
   - 适合 ✔ / 需接受 ✖ 提示
   - **历史报价**列表：
     - 每条显示：报价单号 + 日期·人数·天数 + 价格
     - 左侧点击 → 打开报价单详情页（`isReview=true`）
     - 右侧操作：🔒 锁定/解锁 + 🗑️ 删除

**交互规则**：
- 最多 3 个方案对比
- 编辑参数后自动生成新报价记录，锁自动移至最新
- 锁定某个报价后，编辑操作基于该报价的参数
- 关闭报价单页时也会生成一条新报价记录

---

## 三、弹窗 / 抽屉

### 3.1 参团二维码弹窗（#qrOverlay）
**触发**: 点击「立即参团」按钮

**结构**：
1. **国家选项卡**: "肯尼亚" / "坦桑尼亚"（可切换，默认肯尼亚）
2. **二维码图片**:
   - 肯尼亚: `qr-kenya.png`
   - 坦桑尼亚: `qr-tanzania.png`
3. **描述文字**: "当前信息已复制\n长按扫码添加客服黏贴对接"

**交互**：
- 打开时自动弹出 **Toast 提示**（屏幕正中央，黑色半透明）：
  - 肯尼亚: `"NeekTrip肯尼亚落地团 预算:400-1500$" 已复制到黏贴板`
  - 坦桑尼亚: `"NeekTrip坦桑尼亚落地团 预算:400-1500$" 已复制到黏贴板`
- 切换选项卡时重复弹出对应 Toast
- 点击蒙层关闭
- 同时将文字信息写入剪贴板

### 3.2 专属顾问二维码弹窗（#advisorQrOverlay）
**触发**: 点击「联系专属顾问」按钮

**结构**：
1. **标题**: "联系专属顾问"
2. **二维码图片**: `qr-advisor.png`
3. **描述文字**: "当前信息已复制\n长按添加顾问黏贴"

**交互**：
- 打开时弹出 **Toast**: `"NeekTrip非洲顶奢定制 预算:7500+$" 已复制到黏贴板`
- 点击蒙层关闭
- 同时将文字信息写入剪贴板

### 3.3 报价单客服二维码弹窗（#serviceQrOverlay）
**触发**: 报价单页底部「联系客服确认行程」按钮

**结构**：
1. **标题**: "联系客服"
2. **二维码图片**: `qr-advisor.png`（复用顾问二维码）
3. **描述文字**: "当前定制信息已复制\n长按扫码添加客服黏贴定制信息"

**交互**：
- 打开时弹出 **Toast**（分行显示，格式如下）：
  ```
  "NeekTrip定制
  昵称：[动态读取]
  目的地：[动态读取]
  出发日期：[动态读取]
  人数：[动态读取]
  天数：[动态读取]
  预算区间：[动态读取]
  BOT报价链接：[当前页面URL]"
  已复制到黏贴板
  ```
- 动态读取报价单头部的参数字段（`quote-guest-name` / `quote-destination` / `quote-departure` / `quote-guests` / `quote-duration` / `quote-budget`）
- **z-index: 3000**（需高于报价单页的 2000）
- 同时将完整文字信息写入剪贴板
- 点击蒙层关闭

### 3.4 定制需求表单抽屉（#formOverlay）
**触发**: 点击预算卡片的「定制xxx方案」按钮

**结构**（底部抽屉，带拖拽指示条）：
1. 标题: "填写定制需求" + 关闭按钮 ×
2. 表单字段：

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| 昵称 | text | 否 | 空 | 默认使用 chatid |
| 目的地 | text（readonly） | 是 | 肯尼亚 | 只读，不可修改 |
| 出发日期 | date | 否 | 空 | 日期选择器 |
| 人数 | number | 否 | 空 | 数字输入 |
| 天数 | number | 否 | 空 | 数字输入 |
| 预算区间 | 双 input | 否 | 空 | 最低 - 最高，由 CTA 按钮预填 |

3. **提交按钮**: "提交需求"

**交互逻辑**：
- 预算的 min/max 由点击的 CTA 按钮预填
- 同一方案名已存在则更新，不重复添加
- 提交后：关闭抽屉 → 生成出行档案书签 → 发送 Bot 气泡 "xxx 基础信息已记录。"（带「查看详细报价单」按钮）→ CTA 按钮状态更新

### 3.5 Toast 提示组件（.qrToast）
- **位置**: 屏幕正中央
- **样式**: 黑色半透明（rgba(0,0,0,0.82)），圆角 12px
- **文字**: 白色，13px，行高 1.6
- **z-index: 4000**（最高层级）
- **自动消失**: 2.2 秒
- **内容**: 支持 `<br>` 换行的 HTML 文本

---

## 四、报价单详情页（Page 2）

### 4.1 导航栏
- **微信小程序风格返回按钮**: SVG 左箭头 + "返回" 文字
  - :active 透明度 0.7 反馈
- **标题**: "专属报价单"（居中显示）
- 导航栏高度 88px（44px 状态栏 + 44px 导航栏）
- 关闭时如非 review 模式，会自动生成一条新报价记录

### 4.2 沉浸式黑卡头部（Hero Section）
- **深色背景**（bg-stone-900）+ 右上角径向渐变装饰
- **右上角**: 语言切换按钮 "中 / EN" + Quote Ref 编号
- **问候语**: "尊敬的 [昵称]"
- **参数网格**（2列）:

| 参数 | 元素 ID | 示例值 | 来源 |
|------|---------|--------|------|
| Destination | quote-destination | 肯尼亚 | plan.params.destination |
| Departure | quote-departure | 未定 | plan.params.date |
| Duration | quote-duration | 7天 | plan.params.days |
| Guests | quote-guests | 2人 | plan.params.people |
| Budget | quote-budget | $2,200 - $2,800 | plan.params.min + max |

- 参数在打开报价单时从当前 plan.params 动态填充

### 4.3 地接社选择模块（Select Provider）
**此模块支持 Sticky 吸顶**，滚动超过后固定在导航栏下方。

#### 4.3.1 标题行
- 标题: "Select Provider"（带星形 SVG 图标）
- 与上方 Hero 区域保持 **24px 间距**（padding-top: 24px）

#### 4.3.2 地接社卡片轮播
- 横向滚动，snap 吸附，每张卡片宽 85%
- **3 个固定指示点**（不与卡片数量绑定，始终 3 个）
- 卡片结构：logo emoji + 标签(Premium/Popular/...) + 名称 + 评分 + 🔒 锁定按钮

**数据来源**: 报价单页面的地接社名单**来自后台「报价管理」模块的「BOT报价列」开关**。后台管理员可在报价管理中为每个地接社设置 BOT 报价列的开关状态，只有开关为「开启」的地接社才会出现在报价单页面的轮播列表中。前端需通过 API 获取当前开启的地接社列表。

> ⚠️ 因此，轮播中的地接社数量不是固定的，可能是3家、5家或更多，取决于后台配置。但指示点始终固定为3个。

**示例地接社数据**（具体数据由后台接口返回）：

| ID | 名称 | Logo | 评分 | 标签 |
|----|------|------|------|------|
| 1 | LionRoar Safari 狮吼东非 | 🦁 | 5.0 | Premium |
| 2 | Savanna Trek 萨凡纳旅行 | 🐘 | 4.9 | Popular |
| 3 | Kilimanjaro Dreams 之梦 | 🏔️ | 4.8 | Classic |
| 4 | Serengeti Pioneers 探索者 | 🐆 | 4.9 | Adventure |
| 5 | Mara Experts 马赛马拉专家 | 🦒 | 4.7 | Local |

**交互**：
- 点击卡片 → 居中选中
- 点击锁定按钮 → 设为基准报价（baseAgencyId）
- 选中卡片样式：深色背景 + 金色标签 + 白色名称
- 未选中：浅色背景 + 半透明

#### 4.3.3 底部操作行
- **左侧**: 3 个轮播指示点（gap: 8px）
- **中间**: 对比提示条（compare-banner-inline）
  - 选中非基准地接社时显示：盾牌图标 + "与 [基准社名] 对比"
  - 使用 max-width 动画横向展开/收起
  - 仅选中与基准不同时可见
- **右侧**: "全部" 按钮 → 打开全部地接社列表抽屉

#### 4.3.4 Sticky 吸顶逻辑
- **实现方式**: JS scroll 监听 + position: fixed（非 CSS sticky，因父容器 overflow 限制）
- **触发条件**: 报价单滚动容器 scrollTop ≥ providerSection 原始位置时吸顶
- **吸顶样式**: position: fixed, top: 88px（导航栏高度），max-width: 448px 居中，box-shadow
- **占位元素**: providerSpacer 在吸顶时显示，高度 = providerSection 高度，防止内容跳动
- **状态标识**: `hasCalculated` 标志位控制位置计算，报价页关闭时完整重置
- **MutationObserver**: 监听 quotePageOverlay 的 class 变化，打开时重算位置

### 4.4 区域1：价格与明细
**白色圆角卡片**，包含：

#### 4.4.1 人均总费用
- 大字展示（5xl），带小数
- 差价标签（diff-total）：选中 vs 基准的差额，红色/绿色

#### 4.4.2 费用分项
| 项目 | 元素 ID 前缀 | 说明 |
|------|-------------|------|
| 交通费用 | val-transport / diff-transport | |
| 住宿费用 | val-accommodation / diff-accommodation | |
| 门票及活动 | val-activities / diff-activities | |
| 服务费 | val-service / diff-service | 最后一条有上边框分隔 |

#### 4.4.3 可折叠明细区
1. **Transport Details**（默认展开）
   - 车型 + 总价/人
   - 服务天数 + 每人每天价格
   - 所有价格项带差价标签
2. **Accommodation Details**（默认展开）
   - 按晚列表：日期 + 酒店名 + 价格/人晚
   - 示例：Night 1 - Tulia Amboseli Camp $132, Night 2 - Tulia Amboseli Camp $145, Night 3 - Lake Nakuru Sopa Lodge $155
   - 所有价格项带差价标签

**折叠/展开交互**：点击标题行，chevron 旋转 180°，内容 grid-template-rows 切换 1fr ↔ 0fr

**差价标签逻辑**：
- 选中 = 基准 → 不显示差价
- 选中 ≠ 基准 → 计算差额，正数红色(+xxx)，负数绿色(-xxx)
- 使用 LCS（最长公共子序列）算法高亮服务描述文字差异

### 4.5 区域2：地接社服务详情
**米色背景卡片**（#f4efe6），包含：

#### 4.5.1 卡片头部
- 盾牌图标 + "Provider Services" + "服务保障与专属福利"

#### 4.5.2 可折叠区：Value Adds（差异化展示）
**数据来源**: 此区域内容**来自后台「地接管理」模块中编辑的「06差异化」模块**。每个地接社在后台地接管理的编辑页面中有「差异化」字段，包含「包含费用」「不含费用」「专属福利赠送」三个子项，前端通过 API 获取并渲染。

- ✅ **包含费用**: 盾牌图标 + 文字描述（来自差异化模块的 included 字段）
- ℹ️ **不含费用**: 圆圈 i 图标 + 文字描述（来自差异化模块的 excluded 字段）
- 🎁 **专属福利赠送**: 礼物图标 + 卡片式展示（来自差异化模块的 perks 字段）

#### 4.5.3 可折叠区：Service Process（SOP 交互模块）
**数据来源**: 此区域内容**来自后台「地接管理」模块中已有的 SOP 模块**。每个地接社在后台地接管理中配置了 SOP 流程数据（阶段名称 + 子节点列表），前端通过 API 获取并渲染为交互式 Tab + Stepper 组件。

**4阶段 Tab** + **Stepper 子节点**（示例数据，实际由后台接口返回）：

| 阶段 | 子节点1 | 子节点2 | 子节点3 |
|------|---------|---------|---------|
| 预定前 | 需求沟通 | 方案定制 | 确认签约 |
| 出行前 | 专属服务群 | 出团通知书 | 行前确认 |
| 出行中 | 专车接机 | 沉浸游玩 | 24h响应 |
| 出行后 | 专车送机 | 服务回访 | 开具发票 |

**交互**：
- 点击 Tab 切换阶段，当前阶段圆点变绿放大 + 标签加粗
- 子节点有 fadeSlideUp 动画
- Tab 之间有连接线

### 4.6 区域3：行程概览
**白色圆角卡片**，包含：
- 卡片头部：文档图标 + "Brief Itinerary" + "精简版游猎动线"
- 时间线列表：
  - Day 1: 05/01 Nairobi ➔ Amboseli (240 km / 4-5 hrs)
  - Day 2: 05/02 Amboseli 全天深度游猎
  - Day 3: 05/03 Amboseli ➔ Lake Nakuru
  - Day 4: 05/04 Lake Nakuru ➔ Maasai Mara
  - Day 10: 05/10 送机启程 ➔ 温暖的家
- 时间线样式：左侧竖线 + 圆点节点

### 4.7 底部操作区
- 有效期提示: "Valid Until 2026/05/30"
- **主按钮**: "联系客服确认行程 →" 
  - 全宽，深色背景（stone-900），白色文字
  - active:scale-95 按压反馈
  - 点击 → 打开报价单客服二维码弹窗（#serviceQrOverlay）

### 4.8 全部地接社列表抽屉（#agency-sheet）
**触发**: 点击 "全部" 按钮

**结构**（底部半屏抽屉）：
- 背景蒙层（半透明 + 模糊）
- 白色面板，顶部圆角 2rem + 拖拽指示条
- 标题: "全部服务提供商" + 关闭按钮
- 列表：5 家地接社，选中项深色背景 + 勾选图标

**交互**：
- 选中某家 → 更新轮播选中 → 关闭抽屉
- 点击蒙层/关闭按钮关闭

---

## 五、数据模型

### 5.1 地接社数据结构
```javascript
{
  id: Number,          // 1-5
  name: String,        // 如 "LionRoar Safari 狮吼东非"
  logo: String,        // emoji 如 "🦁"
  rating: String,      // 如 "5.0"
  label: String,       // 如 "Premium"
  services: {
    included: String,  // 包含费用
    excluded: String,  // 不含费用
    perks: String      // 专属福利
  }
}
```

### 5.2 地接社价格数据结构
```javascript
{
  total: Number,           // 人均总费用
  transport: Number,       // 交通费用
  transportDaily: Number,  // 每人每天交通
  accommodation: Number,   // 住宿总费用
  h1n1: Number,            // 酒店1 晚1
  h1n2: Number,            // 酒店1 晚2
  h2n1: Number,            // 酒店2 晚1
  activities: Number,      // 门票活动
  service: Number          // 服务费
}
```

### 5.3 方案数据结构（plansData）
```javascript
{
  planName: String,     // 如 "经典方案（均衡型）"
  params: {
    nickname: String,
    destination: String,
    date: String,
    people: String,
    days: String,
    min: String,         // 预算最低
    max: String          // 预算最高
  },
  proText: String,      // 优势描述
  conText: String,      // 需接受描述
  quotes: [{            // 历史报价列表
    id: String,
    price: String,      // 如 "$2,614"
    params: Object      // 该报价对应的参数快照
  }]
}
```

### 5.4 SOP 数据结构
```javascript
[{
  stageName: String,    // 如 "预定前"
  subNodes: [{
    title: String,      // 如 "需求沟通"
    desc: String        // 如 "1对1管家深入了解您的出行偏好与预算"
  }]
}]
// 共4个阶段，每阶段3个子节点
```

---

## 六、前端页面路由与组件拆分

> **⚠️ 重要**: 报价单详情页是前端独立页面，非后端渲染。所有 UI、交互、数据计算均由前端完成。

### 6.1 页面路由

| 路由路径 | 页面 | 说明 |
|----------|------|------|
| `/pages/chat/index` | 聊天主页 | 默认首页，包含预算轮播、消息流、输入区 |
| `/pages/quote/index` | 报价单详情页 | 全屏覆盖式页面（非新路由），从聊天页覆盖展示 |

**报价单页面打开方式**: 通过页面内 overlay 全屏覆盖（`v-if` 或 `v-show` 控制），不使用 `Taro.navigateTo`，这样关闭时可回传数据（生成报价记录）。

### 6.2 组件拆分建议

```
src/
├── pages/
│   ├── chat/
│   │   ├── index.vue              # 聊天主页
│   │   ├── index.config.js
│   │   └── index.module.less
│   └── quote/
│       ├── index.vue              # 报价单详情页（overlay 覆盖）
│       ├── index.config.js
│       └── index.module.less
│
├── components/
│   ├── BudgetCarousel/            # 预算卡片轮播
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── BudgetCard/                # 单张预算卡片
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── ProfileBookmark/           # 出行档案书签
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── ChatBubble/                # 聊天气泡
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── QrModal/                   # 二维码弹窗（参团/顾问/客服复用）
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── FormDrawer/                # 定制需求表单抽屉
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── Toast/                     # 黑色透明提示
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── QuoteHero/                 # 报价单黑卡头部
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── ProviderSelector/          # 地接社选择（轮播+Sticky+对比）
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── AgencyCard/                # 地接社卡片
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── AgencySheet/               # 全部地接社列表抽屉
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── PriceBreakdown/            # 价格与明细卡片
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── CollapsibleSection/        # 可折叠区（通用）
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── ServiceDetails/            # 地接社服务详情卡片
│   │   ├── index.vue
│   │   └── index.module.less
│   ├── SopInteractive/            # SOP 交互模块（Tab+Stepper）
│   │   ├── index.vue
│   │   └── index.module.less
│   └── ItineraryTimeline/         # 行程概览时间线
│       ├── index.vue
│       └── index.module.less
│
├── store/
│   ├── chat.js                    # 聊天状态（消息列表、当前方案等）
│   ├── plan.js                    # 方案管理（plansData、activePlanIndex、lockedQuoteId）
│   └── quote.js                   # 报价单状态（selectedAgencyId、baseAgencyId）
│
├── apis/
│   ├── chat.js                    # Bot 对话接口
│   ├── quote.js                   # 报价相关接口（价格计算、地接社列表等）
│   └── clipboard.js               # 剪贴板操作封装
│
└── utils/
    ├── diff.js                    # LCS 差异算法（地接社服务文字对比）
    └── price.js                   # 价格格式化工具
```

### 6.3 Pinia Store 数据流

```
chatStore                           planStore                         quoteStore
┌─────────────────┐                ┌─────────────────┐               ┌─────────────────┐
│ messages[]       │                │ plansData[]      │               │ selectedAgencyId │
│ isQuoteOpen      │───────────────>│ activePlanIndex  │──────────────>│ baseAgencyId     │
│ isFormOpen       │   传参给       │ lockedQuoteId    │   传参给       │ agencies[]       │
│ isQrOpen         │   报价单       │ isCollapsed      │   报价单       │ agencyPrices{}   │
└─────────────────┘                └─────────────────┘               └─────────────────┘
       │                                  │                                  │
       ▼                                  ▼                                  ▼
  BudgetCarousel                  ProfileBookmark                    ProviderSelector
  ChatBubble                      FormDrawer                         PriceBreakdown
  QrModal                         (参数编辑/报价生成)                  ServiceDetails
  FormDrawer                                                         SopInteractive
                                                                     ItineraryTimeline
```

### 6.4 关键数据传递路径

| 场景 | 数据来源 | 数据去向 | 传递方式 |
|------|---------|---------|---------|
| 打开报价单 | `planStore.plansData[activePlanIndex].params` | `QuoteHero` 6个参数字段 | props 传递 |
| 参数编辑 | `ProfileBookmark` contenteditable | `planStore` → 生成新 quote | store action |
| 地接社选中 | `quoteStore.selectedAgencyId` | `PriceBreakdown` + `ServiceDetails` | computed/watch |
| 锁定基准 | 点击 AgencyCard lock 按钮 | `quoteStore.baseAgencyId` | store action |
| 关闭报价单 | 非review模式 | `planStore` 新增 quote 记录 | store action |
| 联系客服 | 读取 QuoteHero 6个参数 | 剪贴板 + Toast + QrModal | ref 读取 |

---

## 七、z-index 层级规范

| 层级 | z-index | 用途 |
|------|---------|------|
| 1 | 1-10 | 报价单内容区元素 |
| 2 | 20 | 地接社选择模块（正常态） |
| 3 | 40 | 全部地接社抽屉蒙层 |
| 4 | 50 | 全部地接社抽屉内容 |
| 5 | 80 | 地接社选择模块（吸顶态） |
| 6 | 1000 | 通用 overlay（参团弹窗、顾问弹窗） |
| 7 | 2000 | 报价单页面（quotePageOverlay） |
| 8 | 3000 | 报价单客服弹窗（serviceQrOverlay） |
| 9 | 4000 | Toast 提示（.qrToast） |

---

## 七、关键交互流程

### 7.1 定制流程
```
点击「定制xxx方案」
  → 打开表单抽屉（预算预填）
  → 填写并提交
  → 关闭抽屉
  → 生成出行档案书签
  → Bot 发送气泡（带「查看详细报价单」按钮）
  → 对应 CTA 按钮置灰
```

### 7.2 报价单查看流程
```
点击「查看详细报价单」
  → 打开报价单页
  → 参数从 plan.params 动态填充到头部
  → 地接社轮播初始化
  → 关闭时：如非 review 模式 → 自动生成报价记录
  → 回到聊天页 → 出行档案更新
```

### 7.3 参数修改流程
```
在出行档案中点击日期/人数/天数
  → contenteditable/date input 编辑
  → blur 或 Enter 提交
  → 基于当前 locked 报价参数生成新参数
  → 自动生成新报价记录（随机价格）
  → 锁自动移至最新报价
  → Bot 发送气泡提示参数变更
```

### 7.4 地接社对比流程
```
选中地接社 A（非基准）
  → 价格明细显示与基准的差价（红/绿色标签）
  → 服务描述用 LCS 算法高亮差异文字
  → 对比提示条展开显示 "与 [基准社名] 对比"
点击锁定按钮 → 设为新基准
  → 差价清零
  → 对比提示条收起
```

### 7.5 参团/顾问联系流程
```
点击「立即参团」
  → 打开参团弹窗（肯尼亚/坦桑尼亚选项卡）
  → Toast 提示 + 剪贴板复制
  → 切换选项卡 → 切换二维码 + 重新 Toast

点击「联系专属顾问」
  → 打开顾问弹窗
  → Toast 提示 "NeekTrip非洲顶奢定制 预算:7500+$" + 剪贴板复制

报价单页点击「联系客服确认行程」
  → 动态读取报价单参数
  → 打开客服弹窗
  → Toast 提示（分行显示完整定制信息） + 剪贴板复制
```

---

## 八、设计规范要点

### 8.1 配色
- 主品牌色: `#A67C52`（焦糖暖棕）
- 标题色: `#1A1A1A`
- 正文色: `#291711`
- 卡片背景: `#FAFAFA`
- 页面背景: `#f7f5f2`
- 深色卡片/导航: `stone-900`
- 金色强调: `#d4af37`
- 绿色正向: `emerald-500 / #12B886`

### 8.2 圆角
- 标准卡片: 24px (`rounded-[2rem]`)
- 按钮: 12px (`rounded-2xl`)
- 小元素/标签: 8px
- 全圆角: 9999px（胶囊按钮/头像）

### 8.3 间距
- 页面左右边距: 40px
- 模块间间距: 24-32px
- 紧凑容器内边距: 16px

### 8.4 字号
- 页面大标题: 48px
- 模块标题: 40px
- 重点卡片标题: 36px
- 列表/正文强调: 32px
- 正文默认: 28px
- 辅助文字: 24px

---

## 九、图片资源清单

| 文件名 | 用途 | 说明 |
|--------|------|------|
| `1500.jpg` | 特种兵王卡片 Hero 背景 | |
| `1500-2200.jpg` | 入门打卡卡片 Hero 背景 | |
| `2200-2800.png` | 经典之选卡片 Hero 背景 | |
| `2800-3500.png` | 深度体验卡片 Hero 背景 | |
| `3500-4500.png` | 小资轻奢卡片 Hero 背景 | |
| `4500-7000.png` | 奢华进阶卡片 Hero 背景 | |
| `7000 +.png` | 顶级定制卡片 Hero 背景 | |
| `qr-kenya.png` | 肯尼亚参团二维码 | JungleRoam 微信二维码 |
| `qr-tanzania.png` | 坦桑尼亚参团二维码 | Kilimanjaro Select 微信二维码 |
| `qr-advisor.png` | 专属顾问/客服二维码 | NeekTrip 顾问微信二维码 |

---

## 十、待确认 / 后端接口依赖

| 项目 | 说明 |
|------|------|
| 价格数据 | 当前为前端硬编码 mock（agencyPrices），需后端 API 返回 |
| 地接社名单 | **来自后台「报价管理」的 BOT报价列开关**，需 API 返回当前开启的地接社列表 |
| 地接社服务详情 | **来自后台「地接管理」的 06差异化模块**，需 API 返回每个地接社的 included/excluded/perks |
| SOP 流程数据 | **来自后台「地接管理」的 SOP 模块**，需 API 返回每个地接社的阶段+子节点数据 |
| 剪贴板复制 | 当前仅 `navigator.clipboard.writeText`，小程序需用 `Taro.setClipboardData`，具体复制内容见第八章附表 |
| 报价单链接 | 当前使用 `window.location.href`，需替换为实际报价单 URL |
| 昵称默认值 | 当前默认 "旅行者"，需从用户登录态获取 |
| 二维码图片 | 当前为占位图，需替换为真实微信二维码（qr-kenya/qr-tanzania/qr-advisor） |
| 报价生成 | 当前 `generatePriceForPlan` 为随机数，需后端实时计算 |
| Chat 输入 | 当前发送按钮无实际功能，需接入 Bot 对话 API |
| 语言切换 | 当前仅切换按钮文案，需实际的中英文切换逻辑 |
