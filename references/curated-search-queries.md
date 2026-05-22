# Social Product Intelligence — Curated Search Queries

## ⚠️ Search engine caveats (added 2026-05-18)

Most search engines (Bing, Google, DuckDuckGo) now use aggressive bot-detection
(Cloudflare, CAPTCHA) against curl/browser automation. Prefer direct press room
navigation over search engines.

**Keywords that work in direct press rooms (not search engines):**
- Product-specific, not topic-generic
- "Tinder Events" > "AI dating social new feature"
- "Hinge Date Ideas" > "social app matching"
- Names of specific features, not categories

```
AI+dating+matchmaking+feature+2026
AI+companion+social+app+loneliness+2026
generative+profile+AI+social+product
AI+icebreaker+conversation+starter+dating+app
AI+agent+friend+dazi+social+platform
```

## Topic: Tinder / Bumble / Hinge product mechanics

```
Tinder+Sparks+2026+product+keynote+features
Bumble+new+feature+relationship+design+2026
Hinge+prompts+matching+algorithm+update+2026
Match+Group+quarterly+earnings+user+growth+2026
dating+app+retention+engagement+metrics+2026
```

## Topic: Chinese social products

```
小红书+社交+关系链+匹配+2026
Soul+app+元宇宙+社交+AI+2026
抖音+社交+搭子+同城+2026
微信+社交+新功能+年轻用户+2026
探探+青藤+二狗+dating+国内+2026
```

## Topic: Youth behavior / social-emotional

```
年轻人+孤独+社交焦虑+2026
搭子文化+轻社交+2026
Z世代+dating+行为+趋势+2026
social+fatigue+GenZ+2026
friendship+recession+loneliness+epidemic+2026
```

## Topic: AI-native product / Vibe Coding

```
vibe+coding+product+prototype+iterate+social+app
AI+agent+product+management+rapid+prototyping
cursor+claude+code+social+app+prototype+2026
no-code+AI+social+product+launch+2026
```

## Topic: Trust / Safety / AI recommendations

```
AI+recommendation+trust+social+product
GEO+生成式引擎优化+社交+推荐+2026
content+moderation+AI+dating+safety+2026
algorithm+transparency+social+app+matching+2026
```

## Useful curl patterns for each topic

Use as terminal command template:
```bash
curl -sL --max-time 10 \
  "https://www.bing.com/search?q=$(echo 'AI+dating+matchmaking+feature+2026' | sed 's/ /+/g')&setlang=zh-Hans" \
  -H "User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36" \
  | sed 's/<[^>]*>//g' | sed '/^$/d' | head -40
```

Switch `setlang=zh-Hans` to `setlang=en-US` for English results on the same query.