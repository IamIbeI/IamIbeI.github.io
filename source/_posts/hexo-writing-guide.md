---
title: Hexo 文章标签、分类和归档教程
date: 2026-10-07 00:54:00
categories:
  - 博客建设
tags:
  - Hexo
  - 写作教程
---

这篇文章介绍如何在 Hexo 文章中设置标签、分类和归档，并说明从 Typora 写作到博客发布的完整流程。

<!-- more -->

## 1. 新建文章

在 Typora 中创建一个 Markdown 文件，并在文件最上方添加 Front Matter。
Front Matter 必须由两行 `---` 包围，且前面不能有其他内容。

```yaml
---
title: 我的第一篇成长记录
date: 2026-10-07 12:00:00
categories:
  - 个人成长
tags:
  - 成长
  - 复盘
---
```

在第二行 `---` 后开始写正文：

```markdown
## 本周经历

这里填写正文。

## 我的思考

这里填写总结和反思。
```

写完后，将文件放入：

```text
source/_posts/
```

例如：

```text
source/_posts/weekly-review-2026-10-07.md
```

## 2. 增加标签

在 Front Matter 的 `tags` 下按列表格式填写标签：

```yaml
tags:
  - 成长
  - 阅读
  - 时间管理
```

一篇文章可以有多个标签。标签适合描述文章涉及的具体主题，例如“阅读”“Spark”“复盘”。

发布后，可以在下面的页面查看所有标签：

```text
https://iamibei.github.io/tags/
```

## 3. 增加分类

在 Front Matter 的 `categories` 下填写分类：

```yaml
categories:
  - 个人成长
```

分类用于表示文章所属的主要领域。建议一篇文章只设置一个主要分类，例如：

- 个人成长
- 技术沉淀
- 阅读笔记
- 年度复盘

发布后，可以在下面的页面查看所有分类：

```text
https://iamibei.github.io/categories/
```

### 设置多级分类

下面的写法表示“技术沉淀”下的“Spark”子分类：

```yaml
categories:
  - 技术沉淀
  - Spark
```

Hexo 会把列表识别为分类层级，而不是两个互相独立的分类。

## 4. 增加归档

归档不需要手动添加字段。Hexo 会根据文章的 `date` 自动按年份和月份整理：

```yaml
date: 2026-10-07 12:00:00
```

发布后，可以在下面的页面查看归档：

```text
https://iamibei.github.io/archives/
```

修改文章时，可以增加更新时间：

```yaml
updated: 2026-10-08 18:30:00
```

`updated` 只表示文章更新时间，不会改变文章原有的归档日期。

## 5. 完整示例

```markdown
---
title: 关于长期成长的一次复盘
date: 2026-10-07 12:00:00
updated: 2026-10-07 12:00:00
categories:
  - 个人成长
tags:
  - 成长
  - 复盘
  - 长期主义
---

这段内容会显示在博客首页。

<!-- more -->

## 背景

记录事情发生的背景。

## 过程

记录自己的实践和思考。

## 总结

记录结论和下一步行动。
```

`<!-- more -->` 上方是首页摘要，下方是进入文章后显示的完整内容。

## 6. 本地预览和发布

本地预览：

```bash
npm run server
```

浏览器访问：

```text
http://localhost:4000
```

确认显示正常后提交并推送：

```bash
git add source/_posts/文章文件名.md
git commit -m "新增文章"
git push
```

推送到 `main` 分支后，GitHub Actions 会自动构建并发布博客。

## 7. 常见错误

- Front Matter 必须位于文件第一行。
- `---`、字段名和冒号必须使用英文符号。
- YAML 缩进使用空格，不要使用 Tab。
- 每个标签和分类前需要写 `-`。
- `date` 建议使用 `YYYY-MM-DD HH:mm:ss` 格式。
- 文章文件必须放在 `source/_posts/` 中才会被 Hexo 发布。
