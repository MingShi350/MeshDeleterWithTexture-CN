# MeshDeleterWithTexture 汉化版

基于 [gatosyocora/MeshDeleterWithTexture](https://github.com/gatosyocora/MeshDeleterWithTexture) v0.10.5 汉化修改。

**原项目 MIT 许可证** | 原作者：[gatosyocora](https://github.com/gatosyocora)

---

## 简介

一个 Unity 编辑器工具：**在模型贴图上直接绘制，标记要删除的网格面**。

常用于 VRChat 模型优化——比如穿模的身体部位、不想显示的装饰部件，画几笔就能精确删掉对应的三角面。

**仅支持 PC Build Target（不支持 Android）。**

---

## 安装

下载 `.unitypackage`，导入 Unity 项目。

导入后路径：`Assets/[MingShi]/MeshDeleterWithTexture/`

菜单入口：`MingShi_/贴图绘制删面`

> 本版本为直接 Assets 安装，不支持 VPM/包管理器导入。

---

## 修改内容

### 中文化
- 新增简体中文语言包（`Resources/MDwT/Lang/ZH.asset`），界面全部汉化
- 语言枚举及加载逻辑已适配中文

### Bug 修复
**原版问题：** 拖入渲染器后贴图栏自动加载第一个材质，画板偶现半边已被涂抹的异常状态，直接删除网格会导致模型大面积缺面。

**原因：** 自动初始化材质时画板 buffer 未正确清空，残留了脏数据。

**修复：** 拖入渲染器后贴图栏不再自动选中材质，显示 `--` 等待用户手动选择。选择材质时触发干净的初始化流程，消除脏数据残留。

---

## 使用方法

1. 打开 `MingShi_/贴图绘制删面`
2. 将场景中的模型（SkinnedMeshRenderer 或 MeshRenderer）拖入 **渲染器** 栏
3. 在 **贴图（材质）** 下拉菜单中选择要操作的材质
4. 选择绘制工具：
   - **笔** — 涂抹要删除的区域（黑色/红/绿/蓝可选）
   - **橡皮** — 擦除涂抹
   - **选择** — 框选区域后批量填充
5. 可调整笔/橡皮大小、反转填充、撤销等
6. 点击 **删除网格**，工具会根据涂抹区域删除对应三角面并输出新网格

**小技巧：** 按住 Shift 可画直线。

---

## 注意事项

- 仅支持 `SkinnedMeshRenderer` 和 `MeshRenderer`
- 不支持 Android Build Target
- 删除操作不可逆，建议提前备份
- 输出的新网格默认保存在 `Assets/` 目录，可在 **输出网格** 区域更改

---

## 致谢

原作者 [gatosyocora](https://github.com/gatosyocora) 开发了这个非常实用的工具，本项目仅在其基础上添加中文支持和 bug 修复。
