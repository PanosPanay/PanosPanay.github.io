---
title: 新建文件
date: 2019-11-20 23:13:18
tags:
- 博客
- GitHub
- Hexo
categories:
- 记录
---

# 新建文件

在根目录下，调用git bash

```bash
hexo new 文件名
```

eg. 新建"test.md"文件，则输入：

```bash
hexo new test
```

回车运行后，创建的文章会出现在`source/_posts`文件夹下，是MarkDown格式

在文章的开头通过如下格式添加必要信息：

```markdown
---
title: 标题	# 自动创建，可修改，与文件名不同，是显示在博客上的标题
date: 日期	# 自动创建，eg.2019-11-20 23:13:18
tags:
- 标签1		# 注意'- 标签'之间的空格，没有空格则博客更新不上去
- 标签2
- 标签3
categories:
- 分类1
- 分类2
---
```

开头下方用markdown格式码正文即可

其余设置见参考文档 https://hexo.io/zh-cn/docs/writing.html 