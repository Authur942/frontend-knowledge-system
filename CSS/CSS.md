# css

## 浮动 `float`



## 百分比 `xx%`

百分比是一种相对于包含块的计量单位。它对图片很有用：如下我们实现了图片宽度始终是容器宽度的50%。

```css
article img {
  float: right;
  width: 50%;
}
```

## display

> 定义元素是否显示，以及控制生成哪种盒模型。

- `inline` 

  - >  内联，不可设置元素的宽和高。

- `inline-block`

  - > 内联盒模型，可设置元素的宽高，需要配合 **vertical-align **属性

- `block`

  - > 块模型，可设置宽高，会占据独立的一行。

- `flex`

  - > 

`inline-block` 使用的注意事项：

1. `vertical-align` 属性会影响到`inline-block` 元素，可以将它的值设置会`top`。
2. 你需要设置每一列的宽度。
3. 如果`HTML`源代码中含有空格的话，那么元素列与列之间会产生缝隙。

## 定位 `position`

- `static`
- `relative`
- `fixed`
- `absolute`

`absolute` 是最棘手的position值。 `absolute` 与 `fixed` 的表现类似，但是它不是相对于视窗而是相对于*最近的“positioned”祖先元素*。如果绝对定位（position属性的值为absolute）的元素没有“positioned”祖先元素，*那么它是相对于文档的` body `元素*，并且它会随着页面滚动而移动。记住一个“positioned”元素是指 position 值不是 `static` 的元素。

## 小技巧

画一个带阴影的三角形

```css
width: 0;
height: 0;
border: {
  bottom: 13px solid #fff;
  right: 10px solid transparent;
  left: 10px solid transparent;
}
filter: drop-shadow(2px -2px 2px rgba(0, 0, 0, .1)); // 倒影效果

// 不使用box-shadow是因为盒子的阴影效果
```



