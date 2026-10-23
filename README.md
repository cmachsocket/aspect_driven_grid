# aspect_driven_grid

纯比例驱动的 Flutter 网格：列数与间距都由容器宽高比派生，零硬编码像素。

- 列数 = `baseColumns × 容器宽高比 / baseRatio`，限位在 `minColumns`~`maxColumns`
- 间距 = 列宽 × `gapRatio`
- item 宽高比由调用方传 `childAspectRatio`

提供三个版本：

| Widget | 场景 |
| --- | --- |
| `AspectDrivenGrid` | 普通等高网格 |
| `SliverAspectDrivenGrid` | 嵌入 `CustomScrollView` |
| `MasonryAspectDrivenGrid` | item 高度不一的瀑布流 |

## 使用

```dart
import 'package:aspect_driven_grid/aspect_driven_grid.dart';

AspectDrivenGrid(
  itemCount: items.length,
  childAspectRatio: 0.75,
  itemBuilder: (context, index) => Card(child: Text(items[index].title)),
)
```

`AspectDrivenGrid` / `MasonryAspectDrivenGrid` 依赖父容器在宽高两个方向都有界（例如 `Scaffold` body、`Column` + `Expanded`），不要直接放进 `SingleChildScrollView` 或 `ListView`。

## 参数

| 参数 | 默认值 | 说明 |
| --- | --- | --- |
| `baseColumns` | `2` | 基准宽高比下的列数 |
| `baseRatio` | `1.0` | 基准宽高比 |
| `gapRatio` | `0.04` | 间距 = 列宽 × 该比例 |
| `childAspectRatio` | `1.0` | item 自身宽/高比（仅 `AspectDrivenGrid` / `SliverAspectDrivenGrid`） |
| `minColumns` | `1` | 列数下限 |
| `maxColumns` | `6` | 列数上限 |

## 安装

本地开发时在应用的 `pubspec.yaml` 中使用 path 依赖：

```yaml
dependencies:
  aspect_driven_grid:
    path: ../aspect_driven_grid
```

仓库推送后可改为 git 依赖：

```yaml
dependencies:
  aspect_driven_grid:
    git:
      url: https://github.com/cmachsocket/aspect_driven_grid.git
```

## License

GPL-3.0
