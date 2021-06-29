​	由W3C提出的方案，可以简便、完整、响应式地实现各种页面布局。已经得到所有浏览器的支持

| 作用在flex容器上 | 作用在flex子项上 |
| ---------------- | ---------------- |
| flex-direction   | order            |
| flex-wrap        | flex-grow        |
| flex-flow        | flex-shrink      |
| justify-content  | flex-basis       |
| align-items      | flex             |
| align-content    | align-self       |

## 1.1 flex-direction

​	用来控制子项整体布局方向，如从左往右、从右往左、从上往下、从下往上

| 取值           | 含义                                                         |
| :------------- | ------------------------------------------------------------ |
| row            | 默认值，显示为行。方向为当前文档水平流方向，默认情况是从左往右 |
| row-reverse    | 显示为行。但方向和row属性值相反                              |
| column         | 显示为列                                                     |
| column-reverse | 显示为列。但方向和column属性值相反                           |

## 1.2 flex-wrap

​	用来控制子项整体单行显示还是换行显示

| 取值         | 含义                                                         |
| ------------ | ------------------------------------------------------------ |
| nowrap       | 默认值，表示单行显示，不换行                                 |
| wrap         | 宽度不足换行显示                                             |
| wrap-reverse | 宽度不足换行显示，但是为从下往上开始，也就是原本换行在下面的子项现在跑到上面 |

## 1.3 flex-flow

​	为flex-direction何flex-wrap的复合写法，表示flex布局的flow流动特性，第一个值表示方向，第二个值表示换行，中间用空格隔开

## 1.4 justify-content

​	justify-content属性决定了主轴方向上子项的对齐和分布方式

| 取值          | 含义                                                         |
| ------------- | ------------------------------------------------------------ |
| flex-start    | 默认值，表现为起始位置对齐                                   |
| flex-end      | 表现为结束位置对齐                                           |
| center        | 表现为居中对齐                                               |
| space-between | 表现为两端对齐。多余的空白间距只在元素中间区域分配           |
| space-around  | 每个flex子项两侧都环绕互不干扰的等宽的空白间距，最终视觉上边缘两侧的空白只有中间空白宽度的一半 |
| space-evenly  | 每个flex子项两侧空白间距完全相等                             |

## 1.5 align-items

​	items指的就是flex子项们，因此align-items指的就是子项们相对于flex容器在侧轴方向上的对齐方式

| 取值       | 含义                 |
| ---------- | -------------------- |
| stretch    | 默认值，flex子项拉伸 |
| flex-start | 表现为容器顶部对齐   |
| flex-end   | 表现为容器底部对齐   |
| center     | 表现为垂直居中对齐   |

## 1.6 align-content

​	如果所有flex子项只有一行，则align-content属性没有任何效果

| 取值          | 含义                                                         |
| ------------- | ------------------------------------------------------------ |
| strech        | 默认值。每一行flex子元素都等比例拉伸。例如，如果共两行flex子元素，则每一行拉伸高度是50% |
| flex-start    | 表现为起始位置对齐                                           |
| flex-end      | 表现为结束为止对齐                                           |
| center        | 表现为居中对齐                                               |
| space-between | 表现为两端对齐                                               |
| space-around  | 每一行元素上下都享有独立不重叠的空白空间                     |
| space-evenly  | 每一行元素都完全上下等分                                     |

## 作用在flex子项上的CSS属性

| 取值        | 含义                                                         |
| ----------- | ------------------------------------------------------------ |
| order       | 可以通过设置order改变某一个flex子项的排序位置。所有子项的默认order属性值是0 |
| flex-grow   | 属性中的grow是扩展的意思，扩展的就是flex子项所占据的宽度，扩展所侵占的空间就是除去元素外的剩余空白间隙。默认值为0 |
| flex-shrink | shrink是“收缩”的意思，flex-shrink主要处理当flex容器空间不足时候，单个元素的收缩比例。默认值是1 |
| flex-basis  | flex-basis定义了在分配剩余空间之前元素的默认大小             |
| flex        | flex属性是flex-grow, flex-shrink, flex-basis的缩写           |
| align-self  | align-self指控制单独某一个flex子项的垂直对齐方式             |