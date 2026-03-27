# 远程内容模板

本目录提供三个可上传到 GitHub 的模板文件：

1. `changelog.json`：更新日志内容
2. `help-center.json`：帮助中心内容
3. `book-sources.json`：书源规则列表

## 1. 更新日志（changelog.json）

结构示例：

```json
{
  "currentVersion": "1.2.0",
  "entries": [
    {
      "version": "1.2.0",
      "date": "2026-03-27",
      "title": "主要功能更新",
      "changes": [
        { "type": "feature", "description": "新增帮助中心窗口" },
        { "type": "improvement", "description": "优化更新日志展示" }
      ]
    }
  ]
}
```

## 2. 帮助中心（help-center.json）

结构示例：

```json
{
  "updatedAt": "2026-03-27",
  "sections": [
    {
      "title": "快速开始",
      "items": [
        { "title": "添加书源", "desc": "在书源管理中同步或添加书源" }
      ]
    }
  ]
}
```

## 3. 书源规则（book-sources.json）

这是一个 `NovelSource[]` 的数组。建议基于现有规则进行修改。

结构示例：

```json
[
  {
    "name": "示例书源",
    "url": "https://example.com",
    "search": {
      "url": "https://example.com/search?q=%s",
      "result": ".result .item",
      "bookName": ".title",
      "author": ".author",
      "latestChapter": ".latest",
      "lastUpdateTime": ".time",
      "status": ".status",
      "category": ".category"
    },
    "book": {
      "url": "https://example.com/book/(.*?)/",
      "bookName": "h1",
      "author": ".author",
      "intro": ".intro",
      "category": ".category",
      "coverUrl": "img.cover"
    },
    "toc": {
      "url": "https://example.com/book/%s/",
      "items": ".chapter-list a",
      "name": "text",
      "url": "href"
    },
    "chapter": {
      "url": "https://example.com/chapter/%s",
      "title": "h1",
      "content": ".content"
    }
  }
]
```

## 配置远程地址

应用会优先读取 `用户数据目录/remote.config.json`，其内容如下：

```json
{
  "changelogUrl": "https://raw.githubusercontent.com/<owner>/<repo>/<branch>/docs/remote/changelog.json",
  "helpCenterUrl": "https://raw.githubusercontent.com/<owner>/<repo>/<branch>/docs/remote/help-center.json",
  "bookSourcesUrl": "https://raw.githubusercontent.com/<owner>/<repo>/<branch>/docs/remote/book-sources.json"
}
```

你也可以使用环境变量覆盖：

- `READER_REMOTE_CHANGELOG_URL`
- `READER_REMOTE_HELP_CENTER_URL`
- `READER_REMOTE_BOOK_SOURCES_URL`
