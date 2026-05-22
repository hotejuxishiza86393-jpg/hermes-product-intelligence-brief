# Social Product Press Rooms & Direct Sources

Direct URLs that bypass search engine bot-detection. These official press rooms
have clean, machine-readable content about product features, launches, and roadmaps.

## 🏆 Dating Apps

| Product | URL | Notes |
|---------|-----|-------|
| **Tinder Pressroom** | https://www.tinderpressroom.com/news | Rich content. Filter by year (2026 available). Each article has detailed product descriptions, UI screenshots, and press quotes. JS-based listing — use `browser_console` with `document.querySelectorAll('a')` to extract article URLs. |
| **Tinder Sparks Keynote** | https://www.tinderpressroom.com/2026-03-12-Tinder-Debuts-Inaugural-Product-Keynote-Tinder-Sparks-2026-Start-Something-New | 10+ major product innovations announced. Key reference. Chemistry (AI daily rec), Events (IRL discovery), Music/Astrology Modes, Learning Mode, Camera Roll Scan, Tinder Connect (Duolingo/Beli/Spotify). |
| **Tinder Events Launch** | https://www.tinderpressroom.com/2026-03-16-Tinder-Launches-Events,-a-New-In-App-Feature,-Bringing-Online-Sparks-Into-Real-Life | Events feature — IRL meetup discovery layer pilot in LA. |
| **Hinge Newsroom** | https://hinge.co/newsroom | Tab-filtered by Product, Research & Advice, Trust & Safety, Company News. |
| **Hinge Product Filter** | https://hinge.co/newsroom?category=product | Direct URL to filter for product-only articles. Shows Date Ideas, Convo Starters, Prompt Feedback, Match Note, and product evolution posts. |
| **Hinge Convo Starters** | https://hinge.co/newsroom/convo-starters | AI-powered personalized first-message suggestions. 35% felt more confident reaching out. 72% of daters prefer a like with a message. Launched US Feb 2026, UK added Feb 23 2026. |
| **Hinge Date Ideas** | https://hinge.co/newsroom/date-ideas-feature | Product: date preference indicators on profiles (15 preset activities: drinks, coffee, walk, museum, arcade, etc.). 82% tester confidence improvement asking someone out. 75% of daters stuck in chats that never became dates. |
| **Hinge AI Guide** | https://hinge.co/newsroom/ai-in-dating | Hinge's guide to using AI in dating — product positioning signal. |
| **Hinge Prompt Feedback** | https://hinge.co/newsroom/prompt-feedback | AI-powered prompt writing help — helps daters write unique profiles without prescriptiveness. |
| **Hinge Your World Prompts** | https://hinge.co/newsroom/your-world-prompts-with-esther-perel | Prompts co-designed with therapist Esther Perel for deeper conversations. |
| **Hinge Match Note** | https://hinge.co/newsroom/match-note | Supports underrepresented daters — share context about identity/dating preferences with matches. |
| **Hinge 2025 Product Evolution** | https://hinge.co/newsroom/hinge-2025-product-evolution | Recap of how daters shaped the product — good for understanding product philosophy trajectory. |
| **Bumble Buzz** | https://bumble.com/the-buzz | Mostly lifestyle content, not product updates. Skip for feature research. |
| **Bumble Press** | https://bumble.com/en/press | Check for press releases about product launches. |
| **Match Group** | https://mtch.com/ | Parent company. Quarterly earnings include user metrics, product roadmaps. |

## 🤖 AI Social Products

| Product | URL | Notes |
|---------|-----|-------|
| **Character.AI Blog** | https://blog.character.ai/ | Official blog with Product, Announcements, Company, Research categories. Accessible and well-structured. |
| **Character.AI April Update** | https://blog.character.ai/pipsqueak2-and-more/ | PipSqueak 2 model, Memory upgrades, Lorebook (worldbuilding tool), DeepSqueak improvements. Article URL does NOT match the blog post title — use `browser_console` with `document.querySelectorAll('article a[href]')` to extract actual post URLs from the listing page. |
| **Character.AI Books** | https://blog.character.ai/cai-books/ | c.ai Books — interactive classic literature as playable characters. |
| **Replika** | https://blog.replika.com/ | Product update blog. |
| **Character.AI Community** | https://community.character.ai/ | May be blocked (ERR_CONNECTION_CLOSED). Have fallback. |

## 🇨🇳 Chinese Social Products

| Product | URL | Notes |
|---------|-----|-------|
| **小红书** | https://www.xiaohongshu.com/explore | Feed-based discovery. Hard to scrape. No public newsroom. Monitor via tech media below. |
| **Soul** | https://www.soulapp.cn/ | No public newsroom found. Labeled as "Gen AI social playground" in store listing. Monitor via 36kr. |
| **36kr 社交频道** | https://36kr.com/search/articles/%E7%A4%BE%E4%BA%A4 | Chinese tech media. Browser-navigable. Use `browser_navigate` directly — renders clean article listings with titles and descriptions. Best source for Chinese social product movement. |
| **36kr 大公司频道** | https://36kr.com/search/articles/%E7%A4%BE%E4%BA%A4%20%E6%96%B0%E5%8A%9F%E8%83%BD | Search 36kr for "社交 新功能" — covers Tantan, Soul, Momo, Qingteng updates. |

## 📰 Tech Media (when press rooms are insufficient)

| Source | URL | Notes |
|--------|-----|-------|
| **TechCrunch (social)** | https://techcrunch.com/category/social/ | General social product news — filter for product mechanics. Cloudflare-prone. |
| **The Verge (social)** | https://www.theverge.com/social-media/ | Use with search for specific products. |
| **Product Hunt** | https://producthunt.com/categories/social-networks | Cloudflare-protected. Hard to access programmatically. |

## 🧠 Youth Behavior Research

| Source | URL | Notes |
|--------|-----|-------|
| **Tinder Gen Z Rituals** | https://www.tinderpressroom.com/2026-02-25-Speaking-in-Signals-How-Gen-Z-Creates-New-Commitment-Rituals | Original research on Gen Z commitment and dating behavior. |
| **Hinge Labs Research** | https://hinge.co/labs | Hinge's in-house research team (PhD researchers + behavioral scientists) — publishes data-backed dating insights. |

## 📋 Search fallback (if press rooms yield nothing)

Prefer `ddgs` CLI (DuckDuckGo search) over browser search:

```bash
pip install ddgs -q 2>/dev/null 2>&1
export PATH="$HOME/Library/Python/3.9/bin:$PATH"
ddgs text -q "Tinder new feature matching AI 2026" -m 5
ddgs news -q "dating app feature launch 2026" -m 5
ddgs text -q "AI companion social app update" -m 5
```

Keywords tested this session:
- "Tinder" alone (not "AI dating") — avoids keyword dilution from the word "AI"
- Product-specific queries work best: "Tinder Events", "Hinge Date Ideas", "Bumble launch"
- Avoid generic "AI dating social new feature" — Bing resolves "AI" as the primary keyword and returns generic AI tool sites

## ⚠️ Chinese product curl search — known dead end

**Do NOT use curl to Bing for Chinese product queries.** Bing's Chinese search page returns 20KB+ of JS boilerplate with zero usable content. This was verified in the 2026-05-18 session across 3 separate Chinese queries (小红书, Soul, 探探). Every query's HTML output was 99% JS instrumentation code.

**Instead, for Chinese products:**
1. Use `browser_navigate` directly to `https://36kr.com/search/articles/社交` — this renders clean article listings
2. Search 36kr with `browser_navigate('https://36kr.com/search/articles/关键词')` for specific products (e.g., `Soul`, `探探更新`)
3. Browser-navigate to Baidu search as last resort — it renders more cleanly than Bing for Chinese queries
4. If ddgs is available, use ddgs CLI with Chinese queries rather than curl to Bing