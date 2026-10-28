# olymp-addons

为 `olymp.sty` 提供扩展包。**无需修改 `olymp.sty` 本身**，只需额外加载对应文件，即可扩展题面命令。

## 特性

- **非侵入式扩展**：不修改 `olymp.sty`，通过附加 `.sty` 文件扩展功能。
- **通信题标题扩展**：提供 `\Communication`、`\FirstRun`、`\SecondRun`、`\InputProtocol`、`\OutputProtocol` 等标题命令，默认仅提供英文文本。
- **中文标题扩展**：将所有标题文本覆盖为中文，包括通信题扩展中提供的标题文本。

## 文件说明

- `olymp-comm.sty`：通信题标题命令扩展。
- `olymp-zh.sty`：中文标题覆盖扩展。

## 使用方法

在导言区中，于 `\usepackage{olymp}` **之后**依次加载：

```latex
\usepackage{olymp}
\usepackage{olymp-comm}
\usepackage{olymp-zh}
```

**注意：加载顺序不能颠倒**，即 `olymp-comm` 必须在 `olymp-zh` 之前加载。

## 在 Polygon 中使用

1. 在 `statements.ftl` 中，按上述顺序添加：

   ```latex
   \usepackage{olymp-comm}
   \usepackage{olymp-zh}
   ```

2. 在题目的 **Statements** 页面中，将 `olymp-comm.sty` 和 `olymp-zh.sty` 上传到 **Statement Resource Files** 一栏。

3. 若在比赛的 **Properties/Files** 中上传，需要为这两个文件名添加 `statements-` 前缀，并同步修改文件开头的 `\ProvidesPackage`；同时，`statements.ftl` 中的 `\usepackage` 也要使用带前缀的包名。

   也就是：

   - 文件名：
     - `olymp-comm.sty` → `statements-olymp-comm.sty`
     - `olymp-zh.sty` → `statements-olymp-zh.sty`
   - 文件开头：
     - `\ProvidesPackage{statements-olymp-comm}`
     - `\ProvidesPackage{statements-olymp-zh}`
   - `statements.ftl`：
     - `\usepackage{statements-olymp-comm}`
     - `\usepackage{statements-olymp-zh}`

   加载顺序同样不能颠倒。

## 注意事项

- 标准加载顺序为：`olymp` → `olymp-comm` → `olymp-zh`。
- 中文扩展会覆盖通信题扩展中的标题文本，因此需要按上述顺序同时加载两者。
- 若在 Polygon 比赛配置中使用了 `statements-` 前缀，请确保**文件名、`\ProvidesPackage` 和 `\usepackage` 三处保持一致**。
