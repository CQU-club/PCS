

# Semantic Ontology and Rule-based Reasoning for Precast Concrete Slab Quality Inspection

[cite_start]本项目包含用于预制混凝土叠合板尺寸质量自动检测的语义本体模型及规则推理引擎文件。本项目旨在提高预制构件质量检测的可复现性，并提供一套从“微观缺陷诊断”到“宏观质量评价”的完整逻辑框架 [cite: 1, 2]。

## 核心文件说明

本仓库包含两个核心文件，共同构成了混合推理系统：

1.  **`PCS.owl` (Ontology & SWRL Rules)**:
    * [cite_start]**描述**: 基于 OWL 2 标准构建的预制构件尺寸质量本体模型 [cite: 1]。
    * [cite_start]**核心逻辑**: 包含 500 多条 SWRL 规则，涵盖了 6 大类构件（轮廓、孔洞、洞口、机电盒、分布筋、桁架筋）在“拼装 (Assembly)”、“生产 (Production)”和“完工 (Completion)”三个阶段的尺寸检测、缺陷溯源及修复建议逻辑 [cite: 3, 4, 19, 45, 563]。
    * **工具**: 建议使用 **Protégé 5.x** 或更高版本打开。

2.  **`PCS_Decision.drl` (Drools Rules)**:
    * **描述**: 基于 Drools 规则语言（DRL）编写的宏观决策文件。
    * **核心逻辑**: 利用 Drools 的“封闭世界假设 (CWA)”弥补 SWRL 的逻辑局限。它负责执行“一票否决”逻辑（若任一子构件存在严重缺陷则判定整板不合格）以及“全局放行”逻辑（若无缺陷则判定合格）。

## 混合推理架构

本项目采用了一种双层推理架构，以应对工程现场复杂的数据逻辑：

* [cite_start]**微观诊断层 (SWRL)**: 运行于开放世界假设 (OWA) 下，擅长根据离散的传感器数据（如 RT-DETR 检测到的坐标和尺寸）进行确定性的缺陷识别和原因分析（如：识别由于模具变形导致的孔洞缩小） [cite: 1, 2, 88]。
* **宏观决策层 (Drools)**: 运行于封闭世界假设 (CWA) 下，负责最终的质检结论判定。它解决了 SWRL 无法在“未发现缺陷”时自动推断“合格”的数学难题。

## 本体架构信息

* [cite_start]**Ontology IRI**: `http://www.semanticweb.org/lqz/ontologies/2025/3/PCS` [cite: 1]
* [cite_start]**Version**: 1.0 [cite: 2]
* [cite_start]**Author**: CQU [cite: 2]
* [cite_start]**Key Classes**: `Construction_element`, `Dimensional_quality`, `Hole`, `Opening`, `Electrical_box`, `Distribution_bar`, `Truss_bar` [cite: 3, 4, 5, 7, 19]。

## 如何使用

1.  **本体查看**: 下载 `PCS.owl`，在 Protégé 中加载。您可以通过 `SWRLTab` 查看所有的检测逻辑。
2.  **规则执行**: 在 Java 后端项目中引入 Drools 依赖，加载 `PCS_Decision.drl`。
3.  [cite_start]**数据映射**: 将传感器获取的构件测量值映射为本体中的 `Data Property`（如 `hasD_Length`），推理引擎将自动输出 `causedBy` (缺陷原因) 和 `has_repair_suggestion` (修复建议) [cite: 10, 34, 119]。

## 引用

如果您在研究中使用了这些文件，请引用相关论文：
> *[此处可填入您的论文引用信息]*

---

### 💡 为什么这样写符合行业惯例？

1.  **明确架构逻辑**：审稿人非常看重您为什么要同时提供两个文件。README 中明确解释了 **SWRL (OWA) 与 Drools (CWA)** 的分工，体现了极高的学术专业性。
2.  [cite_start]**提供元数据**：清晰列出了 IRI、版本和作者 [cite: 1, 2]，这符合 **FAIR 原则**（可发现、可访问、可互操作、可重用）。
3.  [cite_start]**使用说明**：README 不仅是文件的陈列，更指导了他人如何利用这些文件构建自己的系统 [cite: 10]。

您可以根据实际的仓库名和论文接收状态对以上内容进行微调。这个 README 配合您的 `.owl` 和 `.drl` 文件，完全符合 `Automation in Construction` 的数据开源政策。
