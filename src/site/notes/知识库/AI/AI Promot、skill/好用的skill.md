---
{"dg-publish":true,"permalink":"//ai/ai-promot-skill/skill/","dg-note-properties":{}}
---

涵盖全网和社媒搜索、社媒读取下载和归档、私人收藏链接导出和音视频ASR转写。  
  
四个核心Skill： 
⓵ yichen-unified-search：Codex的眼镜——全网+社媒搜索，适合深度思考问题、查找实时信息、搜寻开源工具...... 
1. 全网网页、新闻、官网：AnySearch 公共搜索。 
2. 法律、金融、学术、安全等垂直领域：AnySearch 垂直搜索。 
3. GitHub：gh search 搜索仓库、代码、Issue 和 PR。
4. 微信公众号：OpenCLI，通过搜狗微信进行匿名公开搜索。 
5. 小红书：OpenCLI，读取Chrome登录态进行站内搜索，需要当轮授权。 
6. 抖音：OpenCLI，读取Chrome登录态进行低频站内搜索，需要当轮授权。
7. 今日头条：OpenCLI，使用专用匿名环境搜索文章和图文内容。
8. X/Twitter：Grok OAuth＋grok-consult，执行X平台公开内容搜索。 
9. B站：bili search，匿名搜索公开视频和相关信息。 
10. YouTube：yt-dlp ytsearch，匿名搜索公开视频，只提取信息和链接。 
11. 小宇宙：AnySearch，通过 site:[http://xiaoyuzhoufm.com](https://t.co/KADcC1lXLl) 搜索公开内容。 
12. 其他指定网站：AnySearch，通过 site:目标域名 搜索已被公开收录的页面。
13. 多关键词批量搜索：AnySearch batch_search，并行搜索多组关键词。
   14.未指定平台的社交媒体讨论：AnySearch 的社交媒体垂直搜索，先发现公开候选。  
  
⓶yichen-content-archive：读取用户直接提供的网页、小红书、抖音、公众号、YouTube、B站和小宇宙链接，并且下载归档。
1. 普通网页：用 Jina Reader 或 Web Reader 提取正文并转换成Markdown。 
2. 小红书：解析网页中的 INITIAL_STATE 获取正文、图片和视频直链，必要时经授权使用登录态。 
3. 抖音：用 Playwright监听视频详情接口，提取元数据和无水印视频地址。 
4. 微信公众号：通过公开文章解析接口读取单篇正文，批量文章使用本地公众号归档工具。 
5. YouTube：用 yt-dlp 读取视频信息，下载视频、音频、字幕或枚举播放列表。 
6. B站：用 bili-cli 读取视频信息，用 yt-dlp 下载视频或枚举合集。
7. 小宇宙：匿名解析单集页面中的音频地址并下载，播客清单需要OpenCLI授权枚举。  
  
⓷yichen-bookmarks-export：只读导出小红书、抖音、X 的私人收藏链接。
1. X：使用本机 Field Theory CLI，读取 Chrome 登录态并调用 X 内部 GraphQL Bookmarks 接口，同步到本地索引后由 Python 脚本导出链接。
2. 小红书：复用已登录的 Chrome 会话，进入收藏页后自动滚动，通过页面 DOM 提取笔记链接并去重，保留 xsec_token，不导出 Cookie。
3. 抖音：复用已登录的 Chrome 会话，滚动收藏列表并解析页面中的 /video/<id> 和 /note/<id> 链接。  
  
⓸yichen-asr：用 Step ASR 或豆包 ASR 转写已有音视频。两者效果差距不大，豆包略微好一点点。
1. 阶跃星辰Step ASR大概一个小时一毛五：[http://stepfun.com](https://t.co/HQWPQUq0G4) 2.火山引擎豆包ASR大概一个小时一块钱：[http://volcengine.com](https://t.co/OYYbb4HiTy)  
  
yichen-web-research Skill相当于一个入口，如果没有特殊指定，你的所有上述相关的操作会自动分配对应的Skill，如果能记住单独Skill的名字，也可以单独调用。  
  
