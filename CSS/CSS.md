# css

## 定位 `position`

- `static`
- `relative`
- `fixed`
- `absolute`

`absolute` 是最棘手的position值。 `absolute` 与 `fixed` 的表现类似，但是它不是相对于视窗而是相对于*最近的“positioned”祖先元素*。如果绝对定位（position属性的值为absolute）的元素没有“positioned”祖先元素，*那么它是相对于文档的` body `元素*，并且它会随着页面滚动而移动。记住一个“positioned”元素是指 position 值不是 `static` 的元素。

