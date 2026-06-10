# Semantic Ontology and Drools Rules for Precast Concrete Slab Dimensional Quality Inspection
# 预制混凝土板尺寸质量检测语义本体与 Drools 规则库

[English Version](#english-version) | [中文版](#中文版)

---

## 中文版

本项目包含用于预制混凝土板尺寸质量自动检测的数字资产，提供了一套将原始检测数据转化为诊断结果和质量决策的逻辑框架。

### 核心文件说明

本仓库包含两个驱动质量控制系统的核心组件：

#### 1. `PCS.owl` (本体与 SWRL 规则集)
* **描述**：基于 OWL 2 标准构建的预制混凝土构件综合语义模型。
* **逻辑范围**：包含全套语义网规则语言 (SWRL) 规则，用于微观层面的缺陷诊断。涵盖六大类构件：**轮廓、孔、洞、机电盒、分布筋、桁架筋**。
* **生命周期阶段**：规则具有阶段感知能力，可针对**拼装 (Assembly)、生产 (Production) 和完工 (Completion)** 三个关键阶段提供专门的诊断和修复建议。

#### 2. `PCS_Decision.drl` (Drools 决策规则)
* **描述**：专为 Drools 规则引擎设计的工业级业务规则文件。
* **逻辑范围**：管理整块构件的宏观决策逻辑。实现了“一票否决”逻辑（若发现严重缺陷则判定整板不合格）和“放行”逻辑（若未发现缺陷则认证为合格）。
* **工程价值**：处理了纯 OWL/SWRL 框架难以实现的复杂逻辑运算（如“非推导即否定”），确保了工厂部署时决策的稳健性。

### 引用

如果您在研究中使用了这些资源，请引用以下论文：
> Vision-knowledge multimodal framework for dimensional quality assessment and decision-making of prefabricated concrete slabs
> https://www.sciencedirect.com/science/article/pii/S0926580526003390

---

## English Version

This repository hosts the digital artifacts for the automated Dimensional quality inspection of precast concrete slabs. It provides the logic-based framework to transform raw inspection data into diagnostic results and global quality decisions.

### Core Files

This repository contains two essential components that drive the quality control system:

#### 1. `PCS.owl` (Ontology & SWRL Rule Set)
* **Description**: A comprehensive semantic model developed using the OWL 2 standard for precast concrete components.
* **Logic Scope**: It contains a full suite of Semantic Web Rule Language (SWRL) rules designed for micro-level defect diagnosis. It covers six major categories of components: **Contours, Holes, Openings, Electrical Boxes, Distribution Bars, and Truss Bars**.
* **Lifecycle Stages**: The rules are context-aware, providing specialized diagnostics and repair suggestions across three critical stages: **Assembly, Production, and Completion**.

#### 2. `PCS_Decision.drl` (Drools Decision Rules)
* **Description**: An industrial-grade business rule file designed for the Drools Rule Engine.
* **Logic Scope**: This file manages the macro-level decision logic for the entire component. It implements the "Veto" logic (rejecting the entire slab if a critical defect is found) and the "Acceptance" logic (certifying a slab as qualified if no defects are identified). 
* **Engineering Value**: It handles complex logical operations (such as "Negation as Failure") that are computationally difficult to implement within pure OWL/SWRL frameworks, ensuring robust decision-making for factory deployment.

### Citation

If you use these artifacts in your research, please cite the following paper:
>Vision-knowledge multimodal framework for dimensional quality assessment and decision-making of prefabricated concrete slabs
>https://www.sciencedirect.com/science/article/pii/S0926580526003390
