# 小程序现有代码字段全量抽取

> 自动从 src/ 目录下所有 .vue / .js / store 文件中抽取
> 抽取时间：2026-05-20

---

## 一、Pinia Store 字段

### store/index.js

**State (ref/reactive):**

| 字段名 | 初始值 |
|--------|--------|
| `userInfo` | `{}` |
| `token` | `getStorageString("Authorization", ""` |

### store/notice.js

**State (ref/reactive):**

| 字段名 | 初始值 |
|--------|--------|
| `unread_count` | `0` |

### store/useGroupComment.js

**State (ref/reactive):**

| 字段名 | 初始值 |
|--------|--------|
| `commentList` | `[]` |
| `page` | `1` |
| `postId` | `""` |
| `pageLoading` | `false` |
| `pageFinished` | `false` |
| `refresherTriggered` | `false` |

### store/useSystem.js

**State (ref/reactive):**

| 字段名 | 初始值 |
|--------|--------|
| `system` | `""` |
| `systemInfo` | `{}` |
| `statusNavBarHeight` | `0` |
| `navBarHeight` | `0` |

---

## 二、API 接口字段

### apis/budget.js

**导出常量/API路径:**

- `API: budget/config`
- `API: share/route`

**导出函数:**

- `getBudgetConfig`
- `saveBudget`

### apis/chatbot.js

**导出函数:**

- `sendChatbotMessage`
- `getChatbotUpdates`
- `getChatbotHistory`

### apis/common.js

**导出常量/API路径:**

- `API: setting`
- `API: wx/qrcode`

**导出函数:**

- `getSetting`
- `getWxQrcode`

### apis/formed.js

**导出常量/API路径:**

- `API: trip/sights`
- `API: trip/hotel`
- `API: trip/tickets`
- `API: trip/plan`
- `API: trip/template/default`
- `API: travel-shares/routes`
- `API: share/route`

**导出函数:**

- `getTripSights`
- `getTripHotel`
- `getTripTickets`
- `createTripPlan`
- `getDefaultTripTemp`
- `getTripPlanByShareCode`
- `ShareRoute`

### apis/guides.js

**导出常量/API路径:**

- `API: guides`
- `API: guide/feed`
- `API: guides`
- `API: guides/${id}`
- `API: guides/delete`
- `API: guide-comments`
- `API: guide-comments`
- `API: guide-comments`
- `API: guide-comments/like`

**导出函数:**

- `getGuides`
- `getGuideFeed`
- `addGuides`
- `getGuidesDetail`
- `guidesDelete`
- `getGuidesComments`
- `addGuidesComment`
- `delGuidesComment`
- `likeGuidesComment`

### apis/officialGroup.js

**导出常量/API路径:**

- `API: notes/official-feed`

**导出函数:**

- `getOfficialGroupList`

### apis/post.js

**导出常量/API路径:**

- `API: home/feed`
- `API: notes`
- `API: notes/update`
- `API: notes/delete`
- `API: places`
- `API: note/comments`
- `API: notes/${id}`
- `API: /page/share`
- `API: comments`
- `API: comment/random`
- `API: comments/delete`
- `API: notes/contact`
- `API: notes/favorite`
- `API: tags`

**导出函数:**

- `getPostList`
- `publishPost`
- `editPost`
- `deletePost`
- `getPlaces`
- `getComments`
- `getPostDetail`
- `getPageShare`
- `commentsPost`
- `commentsRandom`
- `commentsDelete`
- `notesContact`
- `notesFavorite`
- `getTags`

### apis/user.js

**导出常量/API路径:**

- `API: user/login`
- `API: me`
- `API: user/update`
- `API: set/user/phone`
- `API: phone`
- `API: upload/token`
- `API: me/notes`
- `API: me/notes/favorites`
- `API: me/comments`
- `API: me/notices`
- `API: messages/unread`
- `API: messages/all`
- `API: feedback`
- `API: wx/template`
- `API: subscribe`
- `API: subscribe/time`

**导出函数:**

- `login`
- `getUserInfo`
- `updateUserInfo`
- `setUserPhone`
- `bindPhone`
- `QiniuToken`
- `getMyPosts`
- `getMyFavorites`
- `getMyCommentPosts`
- `getMyNotices`
- `getUnreadNotices`
- `getAllNotices`
- `postFeedBack`
- `getSubTempId`
- `subscribe`
- `subscribeTime`

---

## 三、页面组件字段（Pages）

### common/webview
> `pages/common/webview/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `pageUrl` | `""` |
| `originalUrl` | `""` |

### formed/index.vue
> `pages/formed/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `isDefault` | `true` |
| `showShare` | `false` |
| `shareCode` | `""` |
| `popupShow` | `false` |
| `pickerType` | `"people"` |
| `showUserInfo` | `{}` |
| `planData` | `{}` |

**computed():**

- `language`
- `displayDays`
- `hotelColumns`
- `carColumns`
- `ticketColumns`
- `resultFeeList`
- `allTotalPrice`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `false` |

### formedPage/chooseCalendar
> `pages/formedPage/chooseCalendar/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `maxDay` | `9` |
| `defaultDate` | `[]` |
| `startDateDefault` | `dayjs(` |
| `disabledStart` | `""` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `true` |

### formedPage/editFormed
> `pages/formedPage/editFormed/components/SelectHotel/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentItinerary` | `0` |
| `list` | `[]` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `item.name` |
| `{{ }}` | `item.price / 100` |

### formedPage/editFormed
> `pages/formedPage/editFormed/components/SelectItinerary/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentItinerary` | `null` |
| `list` | `[]` |

**defineProps:**

- `prevSight`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `item.to_sight.name_zh` |
| `{{ }}` | `toFloat(item.distance_km)` |
| `{{ }}` | `toFloat(item.duration / 60, 1)` |

### formedPage/editFormed
> `pages/formedPage/editFormed/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `planData` | `getStorageJson("tripPlan", null` |
| `routeParams` | `null` |
| `chooseType` | `""` |
| `tickets` | `[]` |
| `ticketCounts` | `{}` |
| `place_show` | `false` |
| `hotel_show` | `false` |
| `currentEditIndex` | `0` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `true` |

### groundConnection/ConnectItem
> `pages/groundConnection/ConnectItem/index.vue`

**defineProps:**

- `item`

**computed():**

- `coverUrl`
- `placeTags`
- `featuresText`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `item?.name` |
| `{{ }}` | `tag.name` |
| `{{ }}` | `item?.slogan` |
| `{{ }}` | `item.grade` |
| `{{ }}` | `item.lang?.join("/")` |

### groundConnection/index.vue
> `pages/groundConnection/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showQrModal` | `false` |
| `authModalRef` | `null` |
| `dataList` | `[]` |
| `page` | `1` |
| `isFinished` | `false` |
| `isLoading` | `false` |
| `refresherTriggered` | `false` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `false` |

### groundConnectionPage/add
> `pages/groundConnectionPage/add/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `canUseCrop` | `false` |
| `qiniuToken` | `""` |
| `showYrName` | `""` |
| `selectYr` | `[]` |
| `showModelPicker` | `false` |
| `timeColumns` | `[]` |
| `loading` | `false` |

### groundConnectionPage/commentDetail
> `pages/groundConnectionPage/commentDetail/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `qiniuToken` | `""` |
| `commentId` | `""` |
| `postInfo` | `{}` |
| `loading` | `false` |
| `publishCommentRef` | `null` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:color` | `defaultColor` |

### groundConnectionPage/commentList
> `pages/groundConnectionPage/commentList/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `qiniuToken` | `""` |
| `scrollIntoView` | `""` |
| `reply_id` | `""` |
| `reply_info` | `{}` |
| `loading` | `false` |
| `publishCommentRef` | `null` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:color` | `defaultColor` |

### groundConnectionPage/components
> `pages/groundConnectionPage/components/Comment/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `likeAnimating` | `false` |

**defineProps:**

- `comment`

**computed():**

- `canDeleteComment`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:model-value` | `comment?.rate` |
| `:comment` | `comment` |
| `{{ }}` | `comment?.user?.nickname || "匿名用户"` |
| `{{ }}` | `comment?.content` |
| `{{ }}` | `comment?.like_count || 0` |
| `{{ }}` | `comment?.sub_comments?.length || 0` |

### groundConnectionPage/components
> `pages/groundConnectionPage/components/CommentMedia/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showVideoModal` | `false` |
| `videoRatioPercent` | `getDefaultVideoRatioPercent(` |

**defineProps:**

- `comment`

**computed():**

- `mediaList`
- `mediaType`
- `videoUrl`
- `videoPoster`
- `videoCardStyle`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:visible` | `showVideoModal` |
| `:topOffset` | `statusNavBarHeight` |

### groundConnectionPage/components
> `pages/groundConnectionPage/components/PublishComment/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `formData` | `createDefaultFormData(` |
| `showModal` | `false` |
| `showVideoModal` | `false` |
| `placeHolder` | `"请从车辆、向导、营地等维度分享您的真实感受..."` |
| `commentInfoRef` | `{}` |
| `videoRatioPercent` | `getDefaultVideoRatioPercent(` |

**computed():**

- `imageValue`
- `hasSelectedImage`
- `hasSelectedVideo`
- `activeMediaType`
- `videoPreviewStyle`
- `videoPreviewPoster`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `v-model` | `formData.rates.expert` |
| `v-model` | `formData.content` |
| `v-model` | `imageValue` |
| `:visible` | `showModal` |
| `:pop-class` | `style.popup` |
| `:placeholder-class` | `style.textareaPlaceholder` |
| `:placeholder` | `placeHolder` |
| `:maxlength` | `500` |
| `:maxSize` | `6` |
| `:maxCount` | `9` |
| `:visible` | `showVideoModal` |

### groundConnectionPage/components
> `pages/groundConnectionPage/components/ShowWechat/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `visible` | `false` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `v-model` | `visible` |
| `:show-menu-by-longpress` | `true` |
| `{{ }}` | `info?.name || ""` |

### groundConnectionPage/components
> `pages/groundConnectionPage/components/SubComment/index.vue`

**defineProps:**

- `guide_id`

**computed():**

- `canDeleteComment`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:comment` | `comment` |
| `{{ }}` | `comment.user.nickname` |
| `{{ }}` | `dayjs(comment.created_at).format("YYYY-MM-DD HH:mm")` |
| `{{ }}` | `comment.content` |

### groundConnectionPage/components
> `pages/groundConnectionPage/components/VideoPreviewModal/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `isVideoLoading` | `false` |
| `resolvedTop` | `16` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:autoplay` | `true` |
| `:muted` | `true` |
| `:show-mute-btn` | `true` |
| `:show-fullscreen-btn` | `false` |
| `:show-play-btn` | `true` |
| `:show-center-play-btn` | `true` |
| `:enable-progress-gesture` | `true` |

### groundConnectionPage/detail
> `pages/groundConnectionPage/detail/CommentCard/index.vue`

**defineProps:**

- `guide_id`

**computed():**

- `commentListNews`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:comment` | `item` |
| `{{ }}` | `commenter_num` |
| `{{ }}` | `comment_num` |

### groundConnectionPage/detail
> `pages/groundConnectionPage/detail/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `postId` | `""` |
| `postInfo` | `{}` |
| `navBarColor` | `"transparent"` |
| `navTitleColor` | `"#FFFFFF"` |
| `navBackColor` | `"#FFFFFF"` |
| `showPlatformQrModal` | `false` |
| `showWechatRef` | `null` |
| `showVideoModal` | `false` |
| `currentVideoUrl` | `""` |
| `isVideoLoading` | `false` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:scroll-y` | `true` |
| `:color` | `navBarColor` |
| `:titleColor` | `navTitleColor` |
| `:backColor` | `navBackColor` |

### guidePackages/budgetCalculator
> `pages/guidePackages/budgetCalculator/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `EXCHANGE_RATE` | `7.13` |
| `cityList` | `[]` |
| `showCitySelector` | `false` |
| `showMonthSelector` | `false` |
| `isRestoring` | `false` |
| `fullConfig` | `null` |
| `identityOptions` | `[]` |
| `customIdentities` | `[]` |
| `showCustomIdentityPopup` | `false` |
| `customIdentityInput` | `""` |

**reactive():**

- **`tripData`**: `{
  placeId: "", // 目的地ID (API Key`
- **`configData`**: `{
  route: {
    title: "", // 推荐路线标题
    desc: "", // 路线简述
    priceUSD: 0, // 预估门票总费用 (USD`
- **`personalData`**: `{
  flight: 6500, // 机票费用 (RMB`

**computed():**

- `currentShoppingHint`
- `costs`
- `tripTotalRMB`
- `personalTotalRMB`
- `totalBudget`
- `tripPercent`
- `personalPercent`
- `personalGroupData`
- `segmentsList`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `v-model` | `tripData.people` |
| `v-model` | `tripData.days` |
| `v-model` | `personalData.flight` |
| `v-model` | `personalData.health` |
| `v-model` | `personalData.sim` |
| `v-model` | `personalData.tips` |
| `v-model` | `personalData.reserve` |
| `v-model` | `customIdentityInput` |
| `v-model` | `showCitySelector` |
| `:visible` | `showCustomIdentityPopup` |
| `:index` | `index` |
| `:visible` | `showMonthSelector` |
| `:columns` | `monthColumns` |
| `{{ }}` | `formatMoney(totalBudget)` |
| `{{ }}` | `tripPercent` |
| `{{ }}` | `getPercent(costs.park, totalBudget)` |
| `{{ }}` | `getPercent(costs.transport, totalBudget)` |
| `{{ }}` | `getPercent(costs.accommodation, totalBudget)` |
| `{{ }}` | `personalPercent` |
| `{{ }}` | `getPercent(personalGroupData.flightVisa, totalBudget)` |
| `{{ }}` | `getPercent(personalGroupData.shopComms, totalBudget)` |
| `{{ }}` | `getPercent(personalGroupData.healthMisc, totalBudget)` |
| `{{ }}` | `tripData.placeName` |
| `{{ }}` | `tripData.month` |
| `{{ }}` | `configData.route.title` |
| `{{ }}` | `configData.route.desc` |
| `{{ }}` | `tripData.days === 1 ? '按 1 天计' : '按 N-1 天计'` |
| `{{ }}` | `configData.route.priceUSD` |
| `{{ }}` | `Math.round(configData.route.priceUSD * EXCHANGE_RATE)` |
| `{{ }}` | `car.name` |

### guidePackages/budgetShare
> `pages/guidePackages/budgetShare/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `pageData` | `null` |
| `budgetShareId` | `''` |

**computed():**

- `tripPercentage`
- `personalPercentage`
- `tripExpensesWithPercent`
- `personalExpensesWithPercent`
- `allExpenses`
- `mainPercentage`
- `chartGradient`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `pageData.title` |
| `{{ }}` | `pageData.sn` |
| `{{ }}` | `pageData.placeName` |
| `{{ }}` | `pageData.people` |
| `{{ }}` | `pageData.days` |
| `{{ }}` | `pageData.accommodation` |
| `{{ }}` | `pageData.routeTitle` |
| `{{ }}` | `pageData.routePath.join(' → ')` |
| `{{ }}` | `mainPercentage` |
| `{{ }}` | `tripPercentage` |
| `{{ }}` | `item.label` |
| `{{ }}` | `item.percent` |
| `{{ }}` | `personalPercentage` |
| `{{ }}` | `formatMoney(pageData.tripTotal)` |
| `{{ }}` | `formatMoney(item.value)` |
| `{{ }}` | `formatMoney(pageData.personalTotal)` |
| `{{ }}` | `formatMoney(pageData.totalEst)` |
| `{{ }}` | `tag` |

### guidePackages/countryComparison
> `pages/guidePackages/countryComparison/index.vue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `spot.name` |
| `{{ }}` | `spot.desc` |

### guidePackages/expenseGuide
> `pages/guidePackages/expenseGuide/index.vue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:enable-flex` | `true` |
| `{{ }}` | `item.price` |
| `{{ }}` | `item.content` |
| `{{ }}` | `item.tag` |
| `{{ }}` | `item.label` |
| `{{ }}` | `item.desc` |
| `{{ }}` | `item.value` |
| `{{ }}` | `item.unit` |

### guidePackages/travelProcess
> `pages/guidePackages/travelProcess/index.vue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `row.label` |
| `{{ }}` | `row.linkLabel` |
| `{{ }}` | `txt` |

### homeV2/index.vue
> `pages/homeV2/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showQrModal` | `false` |
| `showJoinGroupModal` | `false` |
| `currentBannerIndex` | `0` |

**computed():**

- `pageVars`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `false` |

### index/CustomizerEntry
> `pages/index/CustomizerEntry/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `isVisible` | `true` |

### index/OfficialGroupCard
> `pages/index/OfficialGroupCard/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showWeChatModal` | `false` |
| `wechatQRCode` | `""` |

**defineProps:**

- `item`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:visible` | `showWeChatModal` |
| `:qr-code` | `wechatQRCode` |
| `:tips` | `wechatTips` |
| `{{ }}` | `item?.guide?.name || "未知旅行社"` |
| `{{ }}` | `item.title || "未知拼团"` |
| `{{ }}` | `formatDays(item.days)` |
| `{{ }}` | `item.location || '未知地点'` |
| `{{ }}` | `formatDate(schedule.date)` |
| `{{ }}` | `formatCode(schedule.code)` |
| `{{ }}` | `formatPrice(schedule.price)` |

### index/PostsItem
> `pages/index/PostsItem/index.vue`

**defineProps:**

- `item`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:userInfo` | `item.user` |
| `:created_at` | `item.created_at` |
| `{{ }}` | `tag.name` |

### index/components
> `pages/index/components/CustomizerEntry/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `isVisible` | `true` |

### index/components
> `pages/index/components/MonthFilter/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showList` | `[]` |

**defineProps:**

- `modelValue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:scroll-x` | `true` |
| `:enhanced` | `true` |
| `:showScrollbar` | `false` |
| `{{ }}` | `item.month` |

### index/components
> `pages/index/components/QrModal/index.vue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:modelValue` | `visible` |
| `:modelValue` | `emit('update:visible', $event)` |
| `:show-menu-by-longpress` | `true` |

### index/components
> `pages/index/components/TopActionTicker/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentIndex` | `0` |
| `isAnimating` | `false` |
| `transitionsEnabled` | `false` |

**defineProps:**

- `items`

**computed():**

- `sourceLength`
- `activePair`
- `currentItem`
- `nextItem`
- `currentContent`
- `nextContent`
- `layerMotion`
- `currentLayerStyle`
- `nextLayerStyle`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `currentContent.subject` |
| `{{ }}` | `currentContent.status` |
| `{{ }}` | `currentItem.actionLabel` |
| `{{ }}` | `nextContent.subject` |
| `{{ }}` | `nextContent.status` |
| `{{ }}` | `nextItem.actionLabel` |

### index/index.vue
> `pages/index/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `activeTab` | `"official-group"` |
| `tabIndex` | `0` |
| `showQrModal` | `false` |
| `showJoinGroupModal` | `false` |
| `dataList` | `[]` |
| `page` | `1` |
| `isFinished` | `false` |
| `isLoading` | `false` |
| `officialGroupList` | `[]` |
| `officialGroupPage` | `1` |
| `officialGroupFinished` | `false` |
| `officialGroupLoading` | `false` |
| `pageHeight` | `500` |
| `filterMethod` | `filterMethodEnum.news` |
| `monthFilterIndex` | `0` |
| `currentMonth` | `""` |
| `authModalRef` | `null` |
| `virtualListRef` | `null` |
| `officialVirtualListRef` | `null` |
| `isRefreshing` | `false` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `false` |

### index/index_old.vue
> `pages/index/index_old.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `pageHeight` | `500` |
| `dataList` | `[]` |
| `page` | `1` |
| `isFinished` | `false` |
| `isLoading` | `false` |
| `virtualListRef` | `null` |

### index/index_origin.vue
> `pages/index/index_origin.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `pageHeight` | `500` |
| `dataList` | `[]` |
| `page` | `1` |
| `isFinished` | `false` |
| `isLoading` | `false` |
| `virtualListRef` | `null` |

### legal/agreement
> `pages/legal/agreement/index.vue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:document-data` | `documentData` |

### legal/components
> `pages/legal/components/LegalDocument/index.vue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `documentData.title` |
| `{{ }}` | `documentData.updatedAt` |
| `{{ }}` | `documentData.effectiveAt` |
| `{{ }}` | `section.heading` |
| `{{ }}` | `paragraph` |

### legal/privacy
> `pages/legal/privacy/index.vue`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:document-data` | `documentData` |

### mine/components
> `pages/mine/components/AddNotice/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `remain` | `0` |

**computed():**

- `progressWidth`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `{{ }}` | `remain < 99 ? remain : "99+"` |

### mine/index.vue
> `pages/mine/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `subVisible` | `false` |
| `remain` | `0` |
| `showUserInfo` | `{}` |
| `showFeedback` | `false` |
| `feedbackBox` | `""` |
| `addWx` | `false` |

**computed():**

- `contorlList`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `false` |

### minePage/editUserInfo
> `pages/minePage/editUserInfo/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `canUseCrop` | `false` |
| `qiniuToken` | `""` |
| `nickName` | `userInfo.nickname` |
| `avatar` | `userInfo.avatar` |

### minePage/myMessageList
> `pages/minePage/myMessageList/MessageItem/index.vue`

**defineProps:**

- `item`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:userInfo` | `item.sender` |
| `:created_at` | `item.created_at` |
| `{{ }}` | `item?.comment?.content || item?.content || item?.comment` |
| `{{ }}` | `item.title` |
| `{{ }}` | `item.note?.date_desc` |
| `{{ }}` | `item?.note?.members` |

### minePage/myMessageList
> `pages/minePage/myMessageList/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `page` | `1` |
| `list` | `[]` |
| `isLoading` | `false` |
| `isFinish` | `false` |
| `navBgColor` | `defaultColor` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:color` | `navBgColor` |

### minePage/myPostList
> `pages/minePage/myPostList/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `page` | `1` |
| `list` | `[]` |
| `isLoading` | `false` |
| `isFinish` | `false` |
| `navBgColor` | `defaultColor` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:color` | `navBgColor` |

### minePage/neekbotChat
> `pages/minePage/neekbotChat/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `messages` | `[]` |
| `draft` | `""` |
| `initialLoading` | `true` |
| `initialLoaded` | `false` |
| `initialPositioned` | `false` |
| `loadingMoreHistory` | `false` |
| `hasMoreHistory` | `false` |
| `nextHistoryOffset` | `0` |
| `updateOffset` | `0` |
| `localUpdateOffset` | `0` |
| `scrollIntoView` | `""` |
| `scrollWithAnimation` | `false` |
| `sending` | `false` |
| `pendingTurns` | `[]` |
| `keyboardHeight` | `0` |
| `windowHeight` | `0` |
| `isOnline` | `true` |
| `isNearBottom` | `true` |
| `typingVisible` | `false` |
| `typingDismissed` | `false` |
| `showManualModal` | `false` |
| `manualQrCode` | `DEFAULT_MANUAL_QR_CODE` |
| `showFeedback` | `false` |
| `feedbackContent` | `""` |

**computed():**

- `canSend`
- `pendingTurnCount`
- `composerSafeBottom`
- `networkBannerHeight`
- `initialMaskTop`
- `showTypingIndicator`
- `showTypingFallback`
- `showScrollToBottomButton`
- `historyTips`

### minePage/shookPostList
> `pages/minePage/shookPostList/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `page` | `1` |
| `list` | `[]` |
| `isLoading` | `false` |
| `isFinish` | `false` |
| `navBgColor` | `defaultColor` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:color` | `navBgColor` |

### postDetail/CommentPopup
> `pages/postDetail/CommentPopup/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `show` | `false` |
| `placeholder` | `"说说你想了解的问题吧..."` |
| `contextData` | `{}` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `v-model` | `formData.content` |
| `v-model` | `formData.imgs` |
| `:visible` | `show` |
| `:visible` | `val => show = val` |
| `:placeholder` | `placeholder` |
| `:maxlength` | `500` |
| `:show-confirm-bar` | `false` |
| `:maxSize` | `6` |
| `:maxCount` | `9` |
| `{{ }}` | `title` |

### postDetail/index.vue
> `pages/postDetail/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `postId` | `""` |
| `qiniuToken` | `""` |
| `comment` | `""` |
| `commentList` | `[]` |
| `page` | `1` |
| `isFinished` | `false` |
| `isLoading` | `false` |
| `reply_id` | `""` |
| `reply_info` | `{}` |
| `loading` | `false` |
| `showShare` | `false` |
| `askModal` | `null` |
| `commentTitle` | `"提问"` |
| `reply_placeholder` | `"说说你想了解的问题吧..."` |
| `showCommentControl` | `false` |
| `showModal` | `false` |
| `postWechat` | `""` |
| `navBgColor` | `defaultColor` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:color` | `navBgColor` |

### publish/index.vue
> `pages/publish/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `qiniuToken` | `""` |
| `postId` | `""` |
| `current_num` | `2` |
| `vacancy_num` | `4` |
| `price` | `""` |
| `identityOptions` | `[]` |
| `customIdentities` | `[]` |
| `showCustomIdentityPopup` | `false` |
| `customIdentityInput` | `""` |
| `showCitySelector` | `false` |
| `showChoosePeople` | `false` |
| `calendarShow` | `false` |
| `defaultDate` | `[]` |
| `startDateDefault` | `dayjs(` |
| `difference` | `""` |
| `disabledStart` | `""` |
| `isLoading` | `false` |
| `resPost_id` | `0` |

**computed():**

- `max_num`

### sharePage/index copy.vue
> `pages/sharePage/index copy.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `isFinished` | `false` |
| `shareImage` | `""` |
| `postInfoDetail` | `{}` |
| `formPage` | `"pub"` |

### sharePage/index.vue
> `pages/sharePage/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `groupQrcode` | `""` |
| `formPage` | `"pub"` |

### showFormed/index.vue
> `pages/showFormed/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `planData` | `{}` |

**computed():**

- `language`
- `hotelColumns`
- `carColumns`
- `ticketColumns`
- `resultFeeList`
- `allTotalPrice`

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:showLf` | `true` |

### welcome/index.vue
> `pages/welcome/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentIndex` | `0` |
| `isRouting` | `false` |

**模板绑定（去重）:**

| 绑定方式 | 表达式 |
|----------|--------|
| `:current` | `currentIndex` |
| `:circular` | `false` |
| `:duration` | `260` |

---

## 四、公共组件字段（Components）

### AskModal
> `components/AskModal/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showModal` | `false` |
| `placeHolder` | `"详细你的问题可以获得准确的回答..."` |
| `commentInfoRef` | `{}` |

### AuthModal
> `components/AuthModal/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showModal` | `false` |

### Avatar
> `components/Avatar/index.vue`

**Props:**

- `userInfo`

### Curtain
> `components/Curtain/index.vue`

### IndexTab
> `components/IndexTab/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `indicatorStyle` | `{}` |

### JoinGroupModal
> `components/JoinGroupModal/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `groupQrcode` | `""` |
| `isLoading` | `false` |

**computed():**

- `resolvedQrCode`

### MarkdownRenderer
> `components/MarkdownRenderer/InlineRenderer.vue`

**Props:**

- `nodes`

### MarkdownRenderer
> `components/MarkdownRenderer/MarkdownNode.vue`

### MarkdownRenderer
> `components/MarkdownRenderer/index.vue`

**Props:**

- `nodes`

**computed():**

- `imageUrls`
- `showAssistantMeta`

### Modal
> `components/Modal/index.vue`

### MonthFilter
> `components/MonthFilter/index.vue`

### MyActionSheet
> `components/MyActionSheet/index.vue`

### Steps
> `components/Steps/index.vue`

**Props:**

- `steps`

### Tabbar
> `components/Tabbar/index.vue`

**computed():**

- `isUnRead`

### Table
> `components/Table/index.vue`

**Props:**

- `data`

### UploadImg
> `components/UploadImg/index.vue`

**Props:**

- `modelValue`

### VirtualList
> `components/VirtualList/VirtualListItem.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `itemRef` | `null` |

### VirtualList
> `components/VirtualList/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `viewPortHeight` | `props.containerHeight` |
| `scrollTop` | `0` |
| `startOffset` | `0` |
| `visibleItems` | `[]` |
| `itemHeights` | `[]` |
| `isAtBottom` | `false` |
| `topItem` | `null` |
| `scrollIntoView` | `null` |
| `lock` | `false` |

### VirtualList
> `components/VirtualList/index_4height.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentScrollTop` | `0` |
| `startIndex` | `0` |
| `endIndex` | `0` |
| `visibleData` | `[]` |
| `scrollIntoView` | `null` |

**computed():**

- `totalHeight`
- `visibleCount`
- `topPadding`
- `bottomPadding`

### VirtualList
> `components/VirtualList/index_old.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentScrollTop` | `0` |
| `startIndex` | `0` |
| `endIndex` | `0` |
| `visibleData` | `[]` |
| `scrollIntoView` | `null` |
| `heightMap` | `{}` |
| `cumulativeHeight` | `[]` |

**computed():**

- `totalHeight`
- `visibleCount`
- `topPadding`
- `bottomPadding`

### WeChatQRModal
> `components/WeChatQRModal/example.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `basicModalVisible` | `false` |
| `customModalVisible` | `false` |
| `noQRModalVisible` | `false` |
| `basicQRCode` | `'https://via.placeholder.com/400x400/07C160/FFFFFF?text=WeChat+QR'` |
| `customQRCode` | `'https://via.placeholder.com/400x400/1AAD19/FFFFFF?text=Custom+QR'` |

### WeChatQRModal
> `components/WeChatQRModal/index.vue`

**computed():**

- `displayTips`

### SelectHotel
> `pages/formedPage/editFormed/components/SelectHotel/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentItinerary` | `0` |
| `list` | `[]` |

### SelectItinerary
> `pages/formedPage/editFormed/components/SelectItinerary/index.vue`

**Props:**

- `prevSight`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentItinerary` | `null` |
| `list` | `[]` |

### Comment
> `pages/groundConnectionPage/components/Comment/index.vue`

**Props:**

- `comment`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `likeAnimating` | `false` |

**computed():**

- `canDeleteComment`

### CommentMedia
> `pages/groundConnectionPage/components/CommentMedia/index.vue`

**Props:**

- `comment`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showVideoModal` | `false` |
| `videoRatioPercent` | `getDefaultVideoRatioPercent(` |

**computed():**

- `mediaList`
- `mediaType`
- `videoUrl`
- `videoPoster`
- `videoCardStyle`

### PublishComment
> `pages/groundConnectionPage/components/PublishComment/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `formData` | `createDefaultFormData(` |
| `showModal` | `false` |
| `showVideoModal` | `false` |
| `placeHolder` | `"请从车辆、向导、营地等维度分享您的真实感受..."` |
| `commentInfoRef` | `{}` |
| `videoRatioPercent` | `getDefaultVideoRatioPercent(` |

**computed():**

- `imageValue`
- `hasSelectedImage`
- `hasSelectedVideo`
- `activeMediaType`
- `videoPreviewStyle`
- `videoPreviewPoster`

### ShowWechat
> `pages/groundConnectionPage/components/ShowWechat/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `visible` | `false` |

### SubComment
> `pages/groundConnectionPage/components/SubComment/index.vue`

**Props:**

- `guide_id`

**computed():**

- `canDeleteComment`

### VideoPreviewModal
> `pages/groundConnectionPage/components/VideoPreviewModal/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `isVideoLoading` | `false` |
| `resolvedTop` | `16` |

### CustomizerEntry
> `pages/index/components/CustomizerEntry/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `isVisible` | `true` |

### MonthFilter
> `pages/index/components/MonthFilter/index.vue`

**Props:**

- `modelValue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `showList` | `[]` |

### QrModal
> `pages/index/components/QrModal/index.vue`

### TopActionTicker
> `pages/index/components/TopActionTicker/index.vue`

**Props:**

- `items`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `currentIndex` | `0` |
| `isAnimating` | `false` |
| `transitionsEnabled` | `false` |

**computed():**

- `sourceLength`
- `activePair`
- `currentItem`
- `nextItem`
- `currentContent`
- `nextContent`
- `layerMotion`
- `currentLayerStyle`
- `nextLayerStyle`

### LegalDocument
> `pages/legal/components/LegalDocument/index.vue`

### AddNotice
> `pages/mine/components/AddNotice/index.vue`

**ref():**

| 字段名 | 初始值 |
|--------|--------|
| `remain` | `0` |

**computed():**

- `progressWidth`
