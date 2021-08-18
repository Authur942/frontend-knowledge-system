# HTML（超文本标记语言）

> 标签

**良好的使用语义化标签**有三个优点：

1. 便于开发。
2. 更加适配移动端。
3. 更利于SEO优化, 增强网页的可访问性。

- `<!DOCTYPE html>` 用于声明文档类型，如今用处不大。

- `<html lang="zh-CN">` 根元素，根节点，lang属性为文档设置的主语言。

- `<head></head>` 该元素的内容对用户不可见，其中包含例如面向搜索引擎的搜索关键字（keyword）、页面描述、CSS样式表和字符编码声明等。

  - `<meta charset="utf-8">`——该元素指定文档使用 UTF-8 字符编码。

  - `<meta name="author" content="john">`

  - `<meta name="description" content="this is a html doucument">`

  - `<meta rel="shortcut icon" href="favicon.ico" type="image/x-icon">` rel属性表示文档与被链接文档之间的关系。

  - `<link rel="stylesheet" href="my-css-file.css">`

  - `<script src="my-js-file.js"></script>` JavaScript文档最好置于</body>之前，以便HTML结构完整加载后才执行。

  - `<title></title>` 该元素设置页面的标题，显示在浏览器标签页上。

- `<body></body>` 该元素包含期望让用户在访问页面时看到的内容，包括文本、图像、视频、游戏、可播放的音轨或其他内容。
