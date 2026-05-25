---
name: product-intelligence-brief
version: "0.8.1"  # 0.8.1: HTML 生成改为强制性——每次 cron 必须执行，不可跳过
description: Daily 3-signal (or 5-item WeChat brief) strategic intelligence for a social/dating product PM. Curates actionable signals from AI-native products, social app mechanics, and youth behavior shifts.
author: hermes-agent
tags: [intelligence, signals, social-product, pm, daily-brief, dating, wechat-morning-brief]
---

# 🧠 Product Intelligence Brief — Social Product Radar

Generate daily intelligence on social product features, growth mechanics, AI-native social products, and youth behavior shifts.

## ✅ When to use

- Daily morning brief ritual (cronjob-friendly)
- User asks "what's happening" in social / dating / youth products
- Pre-sprint planning research
- Competitive landscape check

## ❌ Do NOT use for

- News aggregation or RSS summaries
- "What happened in AI today" without product implications
- Academic research with no actionable output
- actionable output
- Generic funding/model/news announcements

## 📐 Output formats

### Format A: 3-Signal Brief (default for generic PM briefs)

```
1. 【信号】TITLE
   - 发生了什么：1-sentence fact
   - 对产品/PM意味着什么：1-sentence implication
   - 可执行动作：1-sentence actionable experiment or next step

2. 【信号】...
3. 【信号】...
```

**RULES:** No preamble/summary/closing. Every signal ends with a concrete action. Chinese only.

### Format B: 5-Item WeChat Morning Brief (for this specific user — social product radar)

Used when the user asks for "社交产品玩法雷达" or "微信晨报". Output up to 5 items.

```
## 📋 晨报摘要
> [一句话：今天社交产品领域最值得关注的核心信号，让读者30秒把握全局]

---

### 🔥 1. [产品名]

📌 **新变化**
[一句话描述，不超过40字]

📊 **为什么重要**
[1-2句用户行为变化分析，忌空话]

💡 **可借鉴**
[1-2句产品洞察或可执行的实验思路]

🔗 [查看原文](url)

🕐 [新鲜度标记] · [时间来源]


---

### 🔥 2. [产品名]
...

---

### 🎯 今日最值得关注
[从以上5条中选1条，1-2句理由说明为什么它最可能影响未来社交产品方向]
```

**RULES:**
- 晨报摘要是必须的，必须放在最前面，用 `>` 引用块格式
- 每条产品用 `### 🔥 N. ` 三级标题 + emoji 分隔，视觉卡片感
- 每个字段独占一行，emoji 标题后换行再写内容，避免文字堆砌
- 每条之间用 `---` 分隔线
- 严禁大段文字段落，每个字段控制在1-2句
- 来源链接必须真实可点击，禁止编造 URL
- 每条末尾必须附加 `🕐 [新鲜度标记] · [时间来源]`，新鲜度按 ⏱️ 时间约束规则判定
- 同一事件被多个来源报道时，在「📌 新变化」末尾合并标注 `（另见：[来源名]）`
- 过去 3 天内已报告过的同一产品事件不再重复输出，除非有重大进展
- **不同产品必须独立成条**：禁止仅因属于同一产品类别而合并为一条。典型错误：把 Replika 和 Character.AI 合成一条「AI 陪伴产品动态」——两者产品机制不同，必须分开独立分析

## 📡 Signal source priority

1. **AI workflow / AI-native products / agents / vibe coding**
2. **成熟社交产品** (Tinder/Bumble/Hinge/Soul/小红书/抖音/探探/Snapchat)
3. **AI社交产品** (Character AI, Replika, AI companion, AI dating)
4. **年轻人社交情绪与行为变化** — 孤独、社交疲惫、搭子文化、亲密关系新形式

### AI 社交产品分析框架

分析 AI 社交产品时，使用「三路径框架」对信号进行分类（参见 `references/ai-social-signals-may2026.md`）：

- **路径A ✅ 关系润滑剂型** — AI 降低既有关系互动成本（多闪小火人、快手火崽崽、Pengu）。已验证，重点追踪用户规模和自创仪式（合养契约/虚拟婚礼等）
- **路径B ⚠️ 社交代理型** — AI 分身替代用户做社交破冰（Second Me、ELYS）。信任门槛高，关注 "不像我" 问题的解决进展
- **路径C 🆕 群成员型** — AI 以群成员身份加入人类互动（Teamily AI）。实验阶段，关注用户是否将 AI 视为 "成员" 或 "工具"

**关键判断：** 对于有存量关系图的平台（抖音、快手），路径A的天花板远高于冷启动新平台。AI 的角色不是创造连接，而是降低维系连接的成本。

## ⏱️ 时间约束（新鲜度优先，但不丢失信息）

1. **初始搜索**：对每个信号源（如 `web_search`），首先尝试 **过去 24 小时**（`time_range: "day"` 或 `qdr:d`）。
2. **结果数量判断**：
   - 如果该信号源返回的相关结果 ≥ 2 条 → 直接采用，标记「🟢 最新」。
- 如果相关结果 < 2 条 → 自动放宽到 **过去 7 天**（`time_range: "week"`），标记「🟡 近7天」。
   - 如果仍然 < 2 条 → 放宽到 **过去 30 天**（`time_range: "month"`），标记「🟠 近30天」。
3. **特殊信源（官方新闻室、头部竞品官网）**：始终抓取最新发布的文章（不设时间窗口），但仅取 top 1。
4. **兜底**：如果某个类别（如 AI 社交产品）完全无结果，则从 `references/curated-search-queries.md` 中回退到经典案例，并标注「📌 近期无动态，此为趋势回顾」。
5. **输出标注**：每条情报末尾注明时间来源。格式：`🟡 近7天 · 来自 YYYY-MM-DD 数据验证`（非当天报道时用实际数据日期替代"近7天"文字）。当天报道用 `🟢 最新 · YYYY-MM-DD 报道`。

## 🔗 去重与合并规则（必须严格执行）

1. **会话内去重**：
   - 记录本任务中已经收集到的信号（产品名 + 事件关键词 + 来源 URL）。
   - 当新信号与已有信号满足以下任一条件时，视为重复：
     a. 产品名相同且事件描述相似度 > 80%（基于 Jaccard 或关键词重叠）。
     b. URL 相同。
     c. 不同 URL 但标题核心短语相同（例如"Tinder 推出 AI 推荐" vs "Tinder 发布 AI 推荐功能"）。

2. **重复处理**：
   - 保留时间戳最新的那个信号。
   - 若多个来源报道同一事件，合并为一条，在"新变化"末尾附加 `（另见：其他来源）`。

3. **跨天去重（长期记忆）**：
   - 对于过去 3 天内已经报告过的同一产品事件，不再重复输出，除非有**重大进展**（需人工判断，技能中可简单规则：新词出现或数据变化）。此功能可选，初期暂不实现。

4. **输出示例**：

```
📌 新变化
宣布取消滑动匹配 + 女性先发消息规则，推出 AI 红娘「Bee」。（另见：Bloomberg, TechCrunch, Engadget）

🟠 近30天 · 来自 2026-05-11 报道
```

> 注意：「另见」只标注主流科技媒体或官方来源（Bloomberg/TechCrunch/NYT/36氪等），不标注 SEO 采集站、个人博客、论坛帖。

## 🔧 Execution method

### Tier 1 (preferred): Browser navigation to official product newsrooms + web_search for breaking news

**Two parallel paths — run both:**

**Path A: Press rooms.** Navigate to official newsrooms and product blogs for structured updates.
1. Pick 3-5 products from the reference list in `references/social-product-press-rooms.md`
2. `browser_navigate` to each press room
3. `browser_snapshot(full=true)` to read article titles
4. `browser_console` with JS to extract article URLs
5. `browser_navigate` to the most promising articles

**Path B: web_search + web_extract for breaking news.** This surfaced the most valuable signals when press rooms were stale or unreachable. Use targeted queries:
- `"Tinder Hinge Bumble new feature dating 2026"` — global dating product updates
- `"AI companion social app dating new feature 2026"` — AI social frontier
- `"抖音 社交 小火人 变现"` — Chinese social monetization
- `"Soul 搭子 AI 社交"` — Chinese dating apps
- Then `web_extract` on the most promising URLs. Works reliably on: NYT, The Atlantic, 36kr mobile (`m.36kr.com/p/<id>`), Sina Finance, Sohu. Does NOT work on: Instagram, YouTube, Facebook posts (skip these).

### Special case: Chinese social products (no press rooms)

Chinese social products (小红书, Soul, 探探, 青藤之恋, 二狗, 抖音社交) have no public press rooms. **Do NOT fall back to curl-to-Bing for Chinese queries** — verified dead end (100% JS boilerplate, zero usable content).

Instead:
1. Navigate browser directly to `https://36kr.com/search/articles/社交` — 36kr renders clean article listings readable by browser_snapshot
2. For specific products: `browser_navigate('https://36kr.com/search/articles/Soul')` or product name
3. For broad Chinese social monitoring: `browser_navigate('https://36kr.com/search/articles/社交 新功能')`
4. Browse and extract article titles about Chinese social product feature launches and user behavior shifts

### Tier 2 (fallback): ddgs CLI search (when no press room exists)

```bash
pip install ddgs -q 2>/dev/null 2>&1  # install if missing
export PATH="$HOME/Library/Python/3.9/bin:$PATH"
ddgs text -q "KEYWORDS" -m 8 -o json
```

Note: `ddgs` SSL errors ("Unsupported protocol version") occur in Python 3.9 environments. When that fails, fall back to Tier 1 entirely.

### Tier 3 (fallback): curl to search engines (least reliable)

```bash
curl -sL --max-time 10 "https://www.bing.com/search?q=KEYWORDS&setlang=en-US" \
  -H "User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36" \
  | sed 's/<script[^>]*>.*<\/script>//g' \
  | sed 's/<style[^>]*>.*<\/style>//g' \
  | sed 's/<[^>]*>//g' \
  | sed '/^[[:space:]]*$/d' \
  | head -80
```

⚠️ Bing/Google returns JS-heavy HTML that's hard to parse. Expect Cloudflare challenges after ~3 queries. Only use this for keyword discovery, not content extraction.

## 📖 Source directory

See `references/social-product-press-rooms.md` for the full directory of:
- Direct press room URLs (Tinder, Hinge, Bumble, Match Group)
- AI social product blogs (Character AI, Replika)
- Chinese social product monitoring sources (小红书, Soul, 36kr)
- Youth behavior research sources
- Product Hunt category and region filters for each

See `references/ai-social-signals-may2026.md` for AI social product frameworks (three-paths model), Douyin social monetization playbook, and additional 36kr search patterns for Chinese social products.

## ⚠️ Pitfalls

- **Ignore generic AI news** (model releases, funding rounds) unless directly impacting social product mechanics
- **Avoid "watch this space" endings** — every signal must have a do-this-week action
- **Search engines are not reliable** — Bing/Google/DuckDuckGo all trigger Cloudflare/CAPTCHA after a few requests. Prefer direct press room navigation.
- **Browser IS the default**, not curl — this is the reverse of the original assumption. Official press rooms have clean, structured content.
- **3-4 product press rooms is enough** per brief. Don't over-scrape. Value is in synthesis, not exhaustiveness.
- **For the WeChat brief format**: do NOT output search logs/process — only the final formatted brief.
- **Tinder Pressroom** has a JS-based article listing. Use `browser_console` to extract actual article URLs from `document.querySelectorAll('a')` — the visible links in the snapshot may not be direct <a> elements.
- **Bumble** doesn't have a product update blog — Bumble Buzz is lifestyle content. Skip it for product feature research.
- **Character.AI** community may be inaccessible (conn closed). Use the official blog at https://blog.character.ai/ instead.
- **curl-to-Bing for Chinese queries is a dead end.** Chinese-language Bing search on macOS returns 20KB+ of JS instrumentation with zero usable article content. Confirmed across 3+ separate queries. Never use this as a data source. Always use browser_navigate to 36kr or other Chinese tech media instead.
- **Character.AI blog article URLs don't match titles.** The URL slug is derived from the article's internal codename, not the published headline (e.g., "April Update: New Model, Memory, and Lorebook" lives at `/pipsqueak2-and-more/`). Always use `browser_console` with `document.querySelectorAll('article a[href]')` to extract actual URLs from the blog listing page.
- **Hinge Date Ideas and Convo Starters** are evergreen signal sources. Both were launched between Feb-Mar 2026 and represent Hinge's ongoing strategy shift from matching efficiency to post-match experience. Check these articles each brief as recurring references.
- **NEVER fabricate or guess article URLs.** After clicking into a 36kr article, always run `browser_console(expression='window.location.href')` to extract the real URL before using it in output. The 36kr article URLs follow the pattern `https://36kr.com/p/<numeric_id>` and cannot be guessed from titles — guessed URLs return 404. Fake URLs break mobile reading in WeChat. Verified 2026-05-19: `/p/3098133128583425` was a guess that returned "数据不存在或已被删除". Real URLs for the same articles were `/p/3787907674053634` and `/p/3799923753825024`.
- **36kr article pages are unstable via browser.** Clicking into individual 36kr articles via `browser_click` frequently returns ERR_CONNECTION_RESET ("连接已重置"), even though the search listing page loads fine. Instead of clicking into articles, use `browser_console` to extract the numeric ID from search result links, then call `web_extract` on the mobile URL `https://m.36kr.com/p/<id>`. The mobile URL format works reliably with web_extract and returns full article content. Verified 2026-05-20: browser navigation to 36kr article returned "连接已重置", but `web_extract('https://m.36kr.com/p/3799120416791808')` returned the complete article.
- **Character.AI blog is intermittently unreachable.** `blog.character.ai` returned ERR_CONNECTION_RESET on multiple attempts (both article pages and the blog listing). This appears to be a location-based access restriction rather than a permanent outage. Use `web_search` with "Character.AI" + specific feature keywords, then `web_extract` on found links as the primary fallback. Do not rely on browser navigation to Character.AI blog as the sole data source.

## 📄 HTML 版本生成 & 发布

**每次生成社交雷达晨报时，必须同时生成 HTML 版本并发布到 Hermes HTML Manager。**

### HTML 模板

使用 `templates/report.html` 模板，替换以下占位符：
- `{date}` — 日期，格式如 `2026年5月22日`
- `{summary}` — 晨报摘要的一句话内容
- `{cards}` — 产品卡片 HTML，每条格式：
```html
<div class="card">
  <div class="card-num">🔥 第 N 条</div>
  <h3>[产品名]</h3>
  <div class="field">
    <div class="field-label">📌 新变化</div>
    <div class="field-body">[一句话描述]</div>
  </div>
  <div class="field">
    <div class="field-label">📊 为什么重要</div>
    <div class="field-body">[1-2句分析]</div>
  </div>
  <div class="field">
    <div class="field-label">💡 可借鉴</div>
    <div class="field-body">[1-2句洞察]</div>
  </div>
  <div class="field">
    <div class="field-label">🔗 来源</div>
    <div class="field-body"><a href="[url]" target="_blank">查看原文 →</a></div>
  </div>
  <div class="time-marker">
    <span class="freshness-badge badge-green">🟢 最新</span> 2026-05-22 报道
  </div>
</div>
```
- `{highlight}` — 「今日最值得关注」的 1-2 句理由

**新鲜度徽章 CSS class 对照：**
- `🟢 最新` → `badge-green`
- `🟡 近7天` → `badge-yellow`
- `🟠 近30天` → `badge-orange`
- `🔵 官方最新` → `badge-blue`

### 发布到 HTML Manager

生成 HTML 后，用以下命令发布：

```bash
# 文件名格式：社交产品雷达-YYYY-MM-DD.html
HTML_FILE="/tmp/hermes-social-radar-$(date +%Y-%m-%d).html"
INBOX_DIR="$HOME/ai-artifacts/html/inbox"
cp "$HTML_FILE" "$INBOX_DIR/"
# 中文解释：将生成的 HTML 报告复制到 HTML Manager 收件箱，inbox watcher 自动摄入
```

**验证：** 文件放入 inbox 后 250ms 内自动摄入到 pages/ 并出现在管理台 http://localhost:3000。

## 🔁 Cronjob setup (this user's specific setup)

This user runs the "社交产品玩法雷达" daily at 8:30 AM Beijing time with the WeChat brief format.

The cron prompt must be fully self-contained (no user present during cron runs). It should:
- Load `references/social-product-press-rooms.md` for URL directory
- Navigate to 3-5 press rooms via browser
- Extract product changes
- Output Format B (5-item WeChat brief)
- **⚠️ 必须同时生成 HTML 版本并发布到 HTML Manager**（见上方「📄 HTML 版本生成 & 发布」）。每次 cron 运行必须执行：生成 HTML → 复制到 `~/ai-artifacts/html/inbox/` → 验证 http://localhost:3000 可见。此项不可跳过，是任务的必选输出。

## ✅ Verification

After generating a brief:
- **For Format A**: "Does every signal have a concrete next action the PM could take this week?"
- **For Format B**: "有没有晨报摘要？每条是否用 🔥 三级标题分隔？字段是否独占一行、无大段文字？来源链接是否真实？"
- **AI social signals**: Classify each AI social signal into the three-paths framework — was the analysis path-correct? If a new path emerges, update the framework reference.
- **Youth behavior signals**: Look for "self-made rituals" evidence (users creating culture around product features) — this is a stronger engagement signal than raw DAU numbers.